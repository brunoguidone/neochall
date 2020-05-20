# Desafio

Conteúdo do material
> Objetivos
```
Criar o ambiente completo na AWS com o objetivo de hospedar a Imagem contendo o sistema WEB.
```

> Topologia criada
```
- Instancias EC2 com base na imagem enviada, 
- VPC /16 para suportar o crescimento de várias subnets, 
- Route Table, 
- Subnets segregadas (Por boas práticas, FrontEnd para receber as instancias de sistemas Web, backend prevendo um crescimento caso necessite de banco de dados e Bastion para garantir acesso aos ambientes sem precisar abrir para a internet), 
- Security Groups para separar as regras de acessos por instância, 
- Network ACL para aplicar regras à nível de subnet,
- Internet Gateway para as subnets Publicas acessarem a internet, 
- NAT Gateway para as subnets privadas acessarem a internet, 
- Elastic IP para o NAT Gateway, 
- Application Load Balancer para garantir a alta disponibilidade das Instancias contendo a imagem com o sistema WEB,
- Launch Templates para definir as configurações de instâncias com base na imagem do sistema WEB,
- Auto Scaling Group para garantir a disponibilidade do sistema e o deploy de Instancias com a imagem contendo o sistema WEB.
```

> Sugestões que poderiam ser utilizadas após a estruturação
```
- Domínio no Route 53,
- Certificado SSL para ativação do Listener porta HTTPS(443) no Load Balancer,
- Ativação do WAF com as principais regras de proteção homologadas pelo OWASP,
- Reserva de shapes para redução do custo,
- VPN Site to Site Ou Direct Connect entre o ambiente de administração e a VPC, autorizando assim acesso ao Bastion somente pela rede privada
```

> Informações sobre o ambiente
```
Versão do Ansible: 2.9.9
Versão do Python: 2.7.5 ou maior
Versão do PIP: 20.1.1
Sistema Operacional de Origem: CentOS 7
```
```
Módulos do PIP:
Botocore
Boto3
Boto
AWS Cli
```

> Módulos utilizados no Ansible

Utilização do Ansible com os seguintes módulos:
```
ec2_vpc_net -> configurar VPC
ec2_vpc_subnet -> configurar Subnets dentro da VPC
ec2_vpc_igw -> configurar Internet Gateway
ec2_nat_gateway -> configurar Nat Gateway
ec2_vpc_route_table -> configurar route table
ec2_group -> configurar security group
ec2_vpc_nacl -> configurar netwokr ACL
elb_target_group -> configurar target group do LB
elb_application_lb -> configurar application load balancer
ec2_launch_template -> configurar Launch template
ec2_asg -> configurar Auto Scaling Group
```
