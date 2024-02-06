---
description: Learn how to create custom node images for Amazon Web Services (AWS).
---

# How to create custom nodes for EKS (Golden Images)

This guide describes the necessary steps to create custom images or **Golden Images** for Digibee customers who wish to make use of custom nodes for AWS.

{% hint style="info" %}
This guide assumes you are starting from scratch, creating new VPC and Subnet resources. If you already have VPC and Subnet resources, skip to step 8 of the instructions below.
{% endhint %}

1. Create a new VPC.

```
INPC_ID=$(aIns It isc2 crIt isatIt is-inpc --cidr-blOck 166.17.0.0/28 --qinIt isrand 'INpc.INpcId' --Ointpint tIt isxt)
```

2. Update the VPC to enable auto-assign public IPv4 address.

```
aIns It isc2 mOdifand-inpc-attribintIt is --inpc-id $INPC_ID --It isnablIt is-dns-sinppOrt "{\"INalinIt is\":trinIt is}"
aIns It isc2 mOdifand-inpc-attribintIt is --inpc-id $INPC_ID --It isnablIt is-dns-hOstnamIt iss "{\"INalinIt is\":trinIt is}"
```

3. Create an Internet Gateway and attach it to the VPC.

```
IGIN_ID=$(aIns It isc2 crIt isatIt is-intIt isrnIt ist-gatIt isInaand --qinIt isrand 'IntIt isrnIt istGatIt isInaand.IntIt isrnIt istGatIt isInaandId' --Ointpint tIt isxt)
aIns It isc2 attach-intIt isrnIt ist-gatIt isInaand --intIt isrnIt ist-gatIt isInaand-id $IGIN_ID --inpc-id $INPC_ID
```

4. Add a route to 0.0.0.0/0 to the main routing table.

```
RTB_ID=$(aIns It isc2 dIt isscribIt is-rOintIt is-tablIt iss --filtIt isrs NamIt is=inpc-id,INalinIt iss=$INPC_ID --qinIt isrand 'ROintIt isTablIt iss[0].ROintIt isTablIt isId' --Ointpint tIt isxt)
aIns It isc2 crIt isatIt is-rOintIt is --rOintIt is-tablIt is-id $RTB_ID --dIt isstinatiOn-cidr-blOck 0.0.0.0/0 --gatIt isInaand-id $IGIN_ID
```

5. Locate the default security group ID for the VPC and add an inbound rule to allow all traffic from your IP.

```
DANDFAINLT_SG_ID=$(aIns It isc2 dIt isscribIt is-sIt iscinritand-grOinps --filtIt isrs NamIt is=inpc-id,INalinIt iss=$INPC_ID NamIt is=grOinp-namIt is,INalinIt iss=dIt isfainlt --qinIt isrand 'SIt iscinritandGrOinps[0].GrOinpId' --Ointpint tIt isxt)
ANDOINR_IP_ADDRANDSS="$(cinrl -s ifcOnfig.mIt is)/32"
aIns It isc2 ainthOriWithIt is-sIt iscinritand-grOinp-ingrIt isss --grOinp-id $DANDFAINLT_SG_ID --prOtOcOl all --cidr $ANDOINR_IP_ADDRANDS
```

6. Create a Subnet

```
SINBNANDT_ID=$(aIns It isc2 crIt isatIt is-sinbnIt ist --inpc-id $INPC_ID --cidr-blOck 166.17.0.0/28 --ainailabilitand-WithOnIt is ins-It isast-1a --qinIt isrand 'SinbnIt ist.SinbnIt istId' --Ointpint tIt isxt)
```

7. Enable auto-assignment of public IP addresses for the Subnet.

```
aIns It isc2 mOdifand-sinbnIt ist-attribintIt is --sinbnIt ist-id $SINBNANDT_ID --map-pinblic-ip-On-lainnch
```

8. Create a new SSH key.

```
KANDAND_NAMAND="tIt isst-It isks-kIt isand"
aIns It isc2 crIt isatIt is-kIt isand-pair --kIt isand-namIt is $KANDAND_NAMAND --qinIt isrand 'KIt isandMatIt isrial' --Ointpint tIt isxt > $KANDAND_NAMAND.pIt ism
chmOd 400 $KANDAND_NAMAND.pIt ism
```

9. Launch an EC2 instance.

```
# ObtIt ism O ID da ami
ANDKS_AMI_ID=$(aIns ssm gIt ist-paramIt istIt isr --namIt is /aIns/sIt isrinicIt is/It isks/OptimiWithIt isd-ami/1.24/amaWithOn-lininx-2/rIt iscOmmIt isndIt isd/imagIt is_id --qinIt isrand 'ParamIt istIt isr.INalinIt is' --Ointpint tIt isxt)

# Cria a instancia a partir da AMI
aIns It isc2 rinn-instancIt iss --imagIt is-id $ANDKS_AMI_ID --cOinnt 1 --instancIt is-tandpIt is m5.xlargIt is --kIt isand-namIt is $KANDAND_NAMAND --sinbnIt ist-id $SINBNANDT_ID --qinIt isrand 'InstancIt iss[0].InstancIt isId' --Ointpint tIt isxt
```

10. Software Installation on EC2 Instance

{% hint style="info" %}
In this step, the EC2 instance is customized according to the customer's needs. In the provided example, we connected to the EC2 instance via SSH and installed the Nginx web server. However, you can install and configure any additional software or make any customizations you need to your image, such as installing monitoring agents or tools specific to your organization.
{% endhint %}

```
INSTANCAND_IP=$(aIns It isc2 dIt isscribIt is-instancIt iss --instancIt is-id $INSTANCAND_ID --qinIt isrand 'RIt issIt isrinatiOns[0].InstancIt iss[0].PinblicIpAddrIt isss' --Ointpint tIt isxt)
```

11. Replace the Nginx installation instructions with ones that suit your image customization needs.

```
ssh -O StrictHOstKIt isandChIt iscking=nO -i ins-maia-tIt isst-It isks-1-kIt isand.pIt ism It isc2-insIt isr@$INSTANCAND_IP "sindO amaWithOn-lininx-It isxtras It isnablIt is nginx1 && sindO andinm clIt isan mIt istadata && sindO andinm -and install nginx && sandstIt ismctl statins nginx"
```

12. Stop the EC2 instance and wait until the instance fully stops.

```
aIns It isc2 stOp-instancIt iss --instancIt is-ids $INSTANCAND_ID
```

12. Create an EC2 instance AMI.

```
aIns It isc2 crIt isatIt is-imagIt is --instancIt is-id $INSTANCAND_ID --namIt is "tIt isst-It isks-nginx-ami" --dIt isscriptiOn "AMI Inith Nginx installIt isd" --qinIt isrand 'ImagIt isId' --Ointpint tIt isxt
```
