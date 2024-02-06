---
description: >-
  Conheça as diferenças e semelhanças entre essas duas tecnologias de
  conectividade
---

# ZTNA versus VPN

A tabela abaixo detalha os principais aspectos entre ZTNA e VPN no contexto da Digibee Integration Platform.

<table data-full-width="true"><thead><tr><th>Critérios</th><th>ZTNA</th><th>VPN</th></tr></thead><tbody><tr><td>Conexão</td><td><p>ZTNA é uma solução de acesso remoto segura que implementa princípios de segurança Zero Trust, o que significa que usuários e dispositivos não são confiáveis ​​por padrão.<br><br></p><p>A ZTNA garantirá que eles tenham acesso a recursos específicos caso a caso.</p><p><br></p></td><td><p>VPN é uma tecnologia usada para criar uma conexão segura e criptografada entre duas redes ou dispositivos pela Internet.<br><br></p><p>Quando um usuário se conecta a uma VPN, o tráfego da Internet é criptografado e roteado através de um túnel seguro até o servidor VPN. O endereço IP do usuário é substituído pelo endereço IP do servidor VPN, o que ajuda a mascarar a identidade e localização do usuário.</p><p><br><br></p></td></tr><tr><td>Confiança e Acesso</td><td>ZTNA segmenta os recursos de rede no nível do aplicativo e só permite que os usuários acessem aplicativos individuais que seus privilégios os autorizam a usar.<br><br>ZTNA autentica o usuário e o dispositivo cada vez que eles fazem uma solicitação para acessar uma parte diferente da rede. Isso torna muito mais difícil o acesso à rede e limita bastante a quantidade de danos que um invasor poderia causar, mesmo que consiga acesso.</td><td><p>As VPNs presumem que, uma vez que um usuário ou dispositivo esteja conectado à rede corporativa, ele será confiável.<br><br>Esses usuários e dispositivos confiáveis ​​recebem acesso ilimitado a toda a rede.</p><p><br></p></td></tr><tr><td>Visibilidade</td><td>A microssegmentação oferecida pela ZTNA dá aos administradores visibilidade sobre quais aplicativos os usuários estão acessando em tempo real.<br><br>Isso permite que os administradores identifiquem rapidamente qualquer comportamento anômalo que possa indicar comprometimento da conta, como um usuário acessando um aplicativo que normalmente não precisaria.<br><br>Além disso, permite que os administradores identifiquem se assinaram algum aplicativo que não está sendo usado ou que está sendo usado por menos pessoas do que eles achavam que seriam necessários, permitindo-lhes reduzir custos com assinaturas desnecessárias.</td><td><p>Quando um usuário se conecta à rede por meio de uma VPN, os administradores de TI ou de segurança podem</p><p>veja apenas se eles acessaram a rede e quando. Eles não podem ver</p><p>em quais aplicativos o usuário entrou ou por quanto tempo</p><p><br><br></p></td></tr><tr><td>Latência e desempenho</td><td>O ZTNA não exige que todo o tráfego seja roteado através de um gateway ou servidor centralizado. O tráfego vai diretamente para o aplicativo<br><br>Em vez disso, o ZTNA usa gateways distribuídos que estão mais próximos do usuário e dos recursos que ele acessa. Isso reduz a latência e melhora o desempenho.</td><td>As VPNs encaminham o tráfego através de vários servidores e depois através de um ponto central no data center corporativo, o que pode causar latência na conexão.<br><br><br></td></tr><tr><td>Escalabilidade aprimorada</td><td>Com o ZTNA, a conexão específica do aplicativo ao usuário é projetada para escalabilidade rápida, mantendo a disponibilidade de alto desempenho e a entrega consistente necessária para soluções de segurança modernas, sem impactar negativamente a experiência do usuário.</td><td><p>Como as VPNs fornecem ao usuário acesso a tudo, as empresas precisam de um</p><p>determinada largura de banda para funcionar sem afetar os fluxos de trabalho.</p></td></tr><tr><td>Integridade do dispositivo</td><td>ZTNA engloba conformidade e integridade do dispositivo às políticas de acesso, oferecendo a opção de excluir sistemas não conformes, infectados ou comprometidos do acesso a aplicativos e dados corporativos. Isso reduz bastante o risco de roubo ou vazamento de dados.</td><td><p>A VPN de acesso remoto não tem conhecimento do estado de integridade de uma conexão/dispositivo. Se um dispositivo comprometido se conectar via VPN, isso poderá afetar o resto da rede.</p><p><br><br></p></td></tr><tr><td>Funcionalidade</td><td>ZTNA protege o acesso entre recursos e também concede acesso a sistemas, serviços e aplicativos com base em políticas definidas.</td><td>As VPNs protegem o acesso entre redes.</td></tr><tr><td>Implementação e Gestão</td><td>Pode ser implementado em fases, de modo que a fase inicial da implementação seja rápida, com interrupção limitada (ou nenhuma) e construída a partir daí.</td><td>Alta complexidade e muito dependente de equipes de infra.</td></tr><tr><td>Adaptabilidade a ambientes modernos</td><td>O ZTNA é mais adequado para ambientes modernos onde aplicativos e recursos estão espalhados por vários serviços em nuvem, pois pode impor controles de acesso granulares, independentemente da localização do recurso.</td><td>As VPNs podem ter dificuldades para acompanhar a natureza dinâmica dos ambientes de TI modernos, especialmente com o surgimento de aplicativos e serviços baseados em nuvem.</td></tr><tr><td>Flexibilidade</td><td>ZTNA oferece mais flexibilidade do que uma VPN tradicional. As soluções ZTNA são baseadas na nuvem, o que significa que podem ser implementadas em praticamente qualquer lugar com pouco impacto na experiência do usuário.</td><td>As VPNs tradicionais exigem mais configuração manual e oferecem menos flexibilidade. No entanto, as VPNs em nuvem oferecem um nível de flexibilidade igual ao ZTNA, embora com um conjunto de recursos limitado.</td></tr></tbody></table>

\


## Comparação de arquitetura

### ZTNA

<figure><img src="https://lh7-us.googleusercontent.com/8J7s-xOAtqXYMPTnLU4qR6jmztF0ALsU8RCqq-izPbJupI6WBkALDrfSeK8YU_-mhcyuAxudiuj3rfkLPetDCe_P1Q9XBWezscgg7NErVrYcgGHcXhX4c51N2gmhspBGTgLfA6Pa2l2UJg3Rt1HuFQY" alt=""><figcaption></figcaption></figure>

\
\


### VPN

<figure><img src="https://lh7-us.googleusercontent.com/D_9r6u5deMgoZfHtjItZxH6PL4Nju_AbAoUx6tP_ABLulr_5srpYKQsjfYb2_4-yY24jge4UGSWo4jtIjd3q1_gpZdVM8bFUDqbYJ4oOP_6H5So0coCoqp79FHaOkzyGaed_d5PXaOymvpNa8CIcIMc" alt=""><figcaption></figcaption></figure>

\
\
\
\
