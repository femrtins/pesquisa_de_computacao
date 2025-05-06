## Análise Comparativa de Tempo de Restauração: Backups Incrementais, Diferenciais e Intercalados


Fernanda Ribeiro Martins
Graduanda em Ciência da Computação
Instituto Federal Catarinense 
Campus Blumenau
fernandamartinsrm@gmail.com
Luiz Ricardo Uriarte
Professor do Instituto Federal Catarinense 
Campus Blumenau
luiz.uriarte@ifc.edu.br

Monique Ellen dos Santos
Graduanda em Ciência da Computação
Instituto Federal Catarinense 
Campus Blumenau
moniqueellen1402@gmail.com


ABSTRACT
The use of backups to save copies of an organization's digital data is a fundamental and necessary practice as a corrective measure against data corruption in situations such as natural disasters, human errors, and hardware and software failures. From these copies, it is possible to recover lost or incorrectly altered data.
The objective of this research is to compare the restoration time between two approaches: incremental-only backups and the alternation of full and incremental backups.
Through Bacula, it is possible to manage backups and data restoration, as well as obtain information regarding the performed operations. As a result, the restoration time was 52,73% shorter when planning a scheme compared to performing only incremental backups, and 18,75% shorter compared to differential backups. However, this approach also demonstrated the need for more storage capacity for this type of procedure.

Keywords
Backups; Incremental; Full; Bacula, Restoration.

RESUMO
A utilização de backups para salvar cópias dos dados digitais de uma organização é uma prática fundamental e necessária como medida corretiva contra a corrupção de dados em situações como  desastres naturais, erros humanos e falhas de hardware e software. A partir dessas cópias, é possível recuperar os dados perdidos ou alterados incorretamente.
O objetivo desta pesquisa é comparar o tempo de restauração entre três abordagens de backups: apenas backups incrementais, a intercalação de backups completos e incrementais e apenas backups diferenciais.
Por meio do Bacula, é possível realizar a gestão de backups e restauração de dados, além de obter informações a respeito das operações realizadas. Como resultado, o tempo de restauração foi 52,73% menor ao planejar um esquema de alternância entre  os backups se comparado a apenas backups incrementais,  e 18,75% menor em relação a backups diferenciais. No entanto, essa abordagem também demonstrou a necessidade de uma maior capacidade de armazenamento para esse tipo de procedimento.
Palavras-chaves
Backups; Incremental; Completo; Bacula; Restauração.

INTRODUÇÃO

Em um contexto de crescente migração do armazenamento de dados físicos para os digitais, torna-se indispensável pesquisar e implementar procedimentos que assegurem a manutenção e a recuperação das informações diante de possíveis incidentes. [1] explicam que o backup é uma maneira eficaz de corrigir uma fonte de dados em caso de corrupção, pois, ao armazenar a cópia dos dados de um dispositivo de armazenamento, possibilita a reconstrução do disco ou a recuperação de arquivos individuais que foram comprometidos.
Existem diferentes tipos de backups, dentre eles o backup completo, que copia todos os dados de uma fonte, o backup incremental, que salva todas as alterações desde o último backup de qualquer tipo [3], e o backup diferencial, que copia todos os dados desde o último backup completo [2]. Ambos os métodos apresentam vantagens e desvantagens que impactam principalmente o espaço disponível de armazenamento e o tempo de execução. Assim, quando falamos de sistemas onde o tempo de restauração dos backups é relevante, se torna necessário avaliar quais abordagem apresentam melhores soluções para o problema.
Para o administração de backup e restauração, existem ferramentas que facilitam esse processo. Como demonstra [5], o Bacula oferece facilidade de uso e automação, além de um tempo de execução elevado em relação a outras ferramentas populares, como Rdiff-backup e Zbackup.
Dessa forma, o objetivo da pesquisa é comparar o tempo necessário para a restauração de dados por meio do Bacula partindo de três abordagens de backup: a restauração a partir de uma sequência de backups incrementais, a restauração a partir de uma intercalação de backups incrementais e completos e a restauração a partir de uma sequência de backups diferenciais.

REFERENCIAL TEÓRICO
Tipos de backup
A perda ou corrompimento de dados em dispositivos de armazenamento podem ocorrer por diversos motivos, como erro de usuário, falhas de disco, problemas em hardware e software, desastres naturais e outras causas externas. Esses incidentes podem  ocasionar sérias consequências, incluindo perda de cliente e encomendas, danos financeiros, prejuízo de tempo e enfraquecimento da imagem de uma empresa no mercado [3]. Diante dos riscos, é fundamental planejar e executar backups regulares, que agem como medida corretiva a esses eventos.
Backup completo
É uma cópia de todos os dados de um sistema de arquivos em um dispositivo de backup.  Por envolver a leitura e gravação de todos os dados armazenados, esse procedimento requer um maior espaço de armazenamento e mais tempo para ser realizado [3]. No entanto, o tempo de restauração a partir do backup completo é mais rápido, pois os dados estão em um único arquivo e o processo se resume à transferência dos dados, sem a necessidade de operações complexas de recuperação.
Backup incremental
É uma cópia das alterações realizadas nos dados desde um determinado ponto de referência, que pode ser um ponto temporal ou um backup completo [2]. Essa abordagem reduz o tempo da operação e o espaço de armazenamento necessário. No entanto, apresenta maior complexidade na recuperação, pois requer o último backup completo e todos os backups incrementais posteriores. O problema se agrava quando um dos dados incrementais é perdido ou corrompido [2]. “De acordo com Chervenak, Vellanki, Kurmas [1998] as restaurações serão mais lentas em um sistema de backup incremental, que deve começar com o último backup completo e aplicar as alterações dos backups incrementais subsequentes’’.
Backup diferencial
É uma cópia de todos os dados que foram modificados desde o último backup completo, funcionando como um backup incremental cumulativo [2].
Em comparação com os outros procedimentos de backups, é mais rápido que um backup completo porém mais lento que um incremental. Em compensação, a sua operação de recuperação é menos complexa em relação ao backup incremental pois requer apenas dois arquivos de backup, embora ainda mais lento que o backup completo [2].

Comparação entre os tipos de backup
Conforme analisado por [3], a escolha de qual tipo de backup executar e quando fazê-lo depende das necessidades específicas do sistema e do que é viável nesse contexto. Dependendo do sistema, pode ser importante minimizar o tempo em que as operações de backup ocorrem, enquanto que em outros casos o tempo de restauração requer maior prioridade. Além disso, o tamanho do espaço de armazenamento também deve ser considerado quando falamos em grandes quantidades de dados e os custos do armazenamento.

Quadro 1 - Comparação entre tipos de backup
Tipo de Backup
Operação de
Escrita/ Leitura
Operação de Restauração
Espaço de Armazenamento
Backup Completo
Lenta
Rápida
Maior
Backup Diferencial
Intermediária
Intermediária
Médio
Backup Incremental
Rápida
Lenta
Menor


Considerando os pontos positivos e negativos de ambas as técnicas, pode ser planejado um esquema de intercalação, onde um backup completo é realizado após uma série de backups incrementais ou diferenciais, e o processo se repete.[1]

Ferramentas de backups e restauração
Ferramentas de backup e restauração são soluções essenciais para automatizar,  simplificar e monitorar esses processos. “Segundo Preston [2007], existem dois tipos de automatização. Um tipo permite seus backups completarem um ciclo completo sem requerer de você uma intervenção manual, como injeção e carregamento de novos volumes. [...]. O segundo tipo de autenticação é na verdade muito mais importante. Esse tipo de automatização faz referência a como o backup “pensa”. Seu processo de backup deve saber fazer o backup sem lhe informar.”
Bacula
Bacula é um software open source baseado em uma estrutura Cliente/Servidor que permite a administração de backups, restaurações e verificação de dados. Oferece diversas opções de configuração de armazenamento, como backup em múltiplos dispositivos, sendo escalável desde computadores únicos até uma rede com vários computadores [4].
Com base em [5], a configuração do Bacula é realizada ao definir informações referentes aos principais componentes do sistema: Diretor, Console, File, Storage e Catalog (Database Server).

Director
Programa que controla todas as operações de backup, restauração, verificação e arquivos, sendo responsável principalmente por executar agendamentos (schedules) e autenticação de conexões. [4, 5]
Console
Programa que fornece ao administrador uma interface para o gerenciamento de jobs, visualização de mensagens e status de informações, realizando assim a comunicação com o programa Director atual.
A interface pode ter tanto por linha de comando (CLI), que apresenta um maior número de funcionalidades, quanto por interface gráfica (GUI). [4, 5]
File Daemon (FD)
Programa responsável por acessar os dados dos arquivos e diretórios do cliente que serão enviados ao Storage Daemon (SD). Faz isso comunicando-se com o programa Director e determinando quais dados do cliente serão utilizados no backup e a forma de armazenamento, transferindo os dados selecionados. [4, 5]
Storage Daemon (SD)
É a parte do sistema que faz a comunicação direta com os meios de armazenamento físico a serem usados para backup e recuperação. Esses meios de armazenamento podem ser discos, nuvem, fitas ou outras mídias. [4, 5]
Catalog (Database Server)
Funciona como um catálogo que armazena os índices (localização) e volume dos arquivos que foram realizados backups, armazenado essas informações em um banco de dados, que atualmente suporta SQLite, MySQL e PostgreSQL. [4, 5]

PROCEDIMENTOS METODOLÓGICOS

  Configuração do Ambiente Virtual
Para a execução dos testes, foi criada uma máquina virtual em um ambiente de simulação (VirtualBox), onde foram instalados o Ubuntu Server e o software Bacula para permitir a simulação de casos de backups e restauração de dados. A máquina foi configurada com com 40GB de disco e 10 MB de memória, fornecendo espaço suficiente para armazenar os backups e dados utilizados nos testes.

 Instalação e configuração do Bacula
Foi realizada a instalação do Bacula em ambiente único com objetivo de simplificar a configuração e a execução dos testes. Assim, foi possível simular um ambiente real em menor escala e gerenciar todos os recursos e  processos em um mesmo local. Para realização dos testes no Bacula foram configurados os principais arquivos do sistema.
No Bacula Director foram definidos o cliente, a forma de armazenamento dos backups e recuperação (Storage), bem como os diretórios a serem incluídos ou excluídos durante os procedimentos (Filesets). Também foram criados os jobs de backup incremental, backup completo e restauração. Os jobs definem e executam tarefas, especificando quais dados serão incluídos, qual cliente será usado, onde os dados serão armazenados e quando o job será executado (Schedule).
No Storage Daemon foram configurados os dispositivos de armazenamento onde os backups e restaurações devem ser armazenados.
No File Daemon foi especificado o nome do cliente, qual o Bacula Director e a porta que deve ser utilizada para a comunicação entre eles.
Além disso, foi instalado na máquina o Webmin, um software para administrar remotamente servidores Linux, com o objetivo de permitir uma visualização gráfica da execução e listagem dos jobs.

Execução dos testes
Os dados utilizados para a realização dos testes foram obtidos por meio de pastas abertas ao público no GitHub. Foram utilizadas no total cerca de 5.6 GB de dados para servirem de base para as abordagens de teste.
Restauração de backups incrementais
Foi realizado um total de sete backups incrementais sequenciais em uma pasta do cliente após um backup total, que serve como ponto de partida para a restauração. Em seguida, foi simulada uma perda de dados significativa de dados na pasta do cliente, para que fosse executada uma operação de restore. Concluída a restauração, os dados retornam ao local original.
Restauração de backups intercalados
Nesta abordagem, os sete backups incrementais foram realizados de forma intercalada com backups completos, de maneira sequencial, em uma pasta do cliente. Assim como na abordagem anterior, foi realizada a simulação de corrompimento dos dados e executada a operação restore, com os dados novamente restaurados na pasta do cliente.
Restauração de backup diferenciais
Da mesma forma que na restauração de backups incrementais, foi realizado um total de sete backups diferenciais posteriores a um backup completo. Em seguida, foi feita a simulação da perda de dados na pasta do cliente e executada a operação de restore.

Coleta dos resultados
O Bacula possui uma configuração de mensagens associadas a um job, permitindo definir como essas mensagens serão manipuladas e enviadas, seja por  e-mail ao usuário ou destinadas a um arquivo [4].  Assim, informações sobre o job, como data e horário de início e término, identificação e nome do job, quantidade de bytes restaurados, tempo de execução e local direcionado, foram obtidos através desse recurso.

RESULTADOS
A partir do primeiro teste de restauração utilizando a abordagem de backup incrementais (ver figura 2), foi obtido um tempo total de execução de 55 segundos. As informações resultantes do procedimento podem ser consultadas na figura 3.


Figura 1 - Lista dos backups executados pela abordagem de backups incrementais


Figura 2 - Mensagem gerada após a execução da restauração pela abordagem de backups incrementais    

Já no segundo teste de restauração, utilizando a abordagem de backup intercalados (ver figura 4), o tempo total de execução foi de 26 segundos. Da mesma forma, as informações resultantes do procedimento podem ser consultadas na figura 4.

Figura 3 - Lista dos backups executados pela abordagem de backups intercalados


Figura 4 - Mensagem gerada após a execução da restauração pela abordagem de backups intercalados    

Por fim, no terceiro teste a abordagem usando apenas backup diferenciais (ver figura 6) resultou em um tempo total de 32 segundos (ver figura 7).

Figura 5 - Lista dos backups executados pela abordagem de backups diferenciais 

Figura 6 - Mensagem gerada após a execução da restauração pela abordagem de backups diferenciais    

Com base nos resultados obtidos, é possível constatar que o tempo de restauração é cerca de 52,73% menor quando se realiza um esquema de intercalação das técnicas de backup em relação a apenas backups incrementais, e 18,75% menor em relação a apenas backups diferenciais.
Entretanto, um problema verificado durante a execução dos testes diz respeito ao espaço de armazenamento. Enquanto que a primeira abordagem utilizou de 5.6 GB de dados, na segunda foram necessários 8.2 GB, resultando em uma aumento de 46,43% no uso de memória. A terceira abordagem, por sua vez, utilizou 9.5 GB. Comparando esta com com a segunda abordagem, que precisou de mais memória, houve uma redução de 15,85% .
Assim, embora a conclusão da comparação do tempo seja favorável à primeira abordagem, é crucial considerar o espaço de armazenamento necessário, pois a escolha de um esquema de backup deve ser feita de maneira a se alinhar com as necessidades particulares do sistema e os recursos disponíveis.

CONCLUSÃO
O trabalho utilizou o Bacula, uma ferramenta de backup, restauração e verificação de dados, para analisar comparativamente o tempo entre duas abordagens de backups: restauração de apenas backups incrementais e restauração de backups incrementais intercalados com backups completos. 
Em um ambiente de virtualização foi possível simular perda e corrupção de dados, realizar a restauração e obter informações relacionadas. 
Os resultados obtidos mostraram que a estratégia de realizar esquemas intercalados teve uma vantagem de 52,73% no tempo de execução em relação apenas aos backups incrementais e 18,75% em comparação com os backups diferenciais. Entretanto, também indicam diferenças consideráveis entre o espaço de disco usado nas operações (ver figura 8), destacando a importância de combinar o planejamento de backups de acordo com as prioridades do sistema.

Figura 8 - Comparação entre tipos de backup

REFERÊNCIAS

Chervenak, A., Vellanki Z. and Kurmas, Z. 1998.  Protecting File Systems: A Survey of Backup Techniques. In Proceedings of the Joint NASA and IEEE Mass Storage Conference. https://www.researchgate.net/publication/2431989_Protecting_File_Systems_A_Survey_of_Backup_Techniques. Acesso em 16-10-2024.
Nadee, P. e Somwang, P. 2021. Efficient incremental data backup of unison synchronize approach. Thailand: Bulletin of Electrical Engineering and Informatics. https://www.researchgate.net/publication/355375926_Efficient_incremental_data_backup_of_unison_synchronize_approach. Acesso em: 16-09-2024.
Preston, W. C. 2007. Backup & Recovery: Inexpensive Backup Solutions for Open Systems. Sebastopol: O’Reilly Media.  Disponível em: https://www.pdfdrive.com/backup-recovery-inexpensive-backup-solutions-for-open-systems-e162525399.html. Acesso em: 16-10-2024.
Sibbald, K. 2024. Bacula Main Reference Manual. Bacula Community Edition v.15.0.2. Disponível em: https://www.bacula.org/15.0.x-manuals/en/main/main.pdf. Acesso em: 19-10-2024.
Reis, D. D. R. A. 2018. Avaliação de ferramentas de backup para implementação em uma organização empresarial. Orientador: Raimundo Viégas Junior. 2018. 61 f. Trabalho de Conclusão de Curso (Bacharelado em Sistemas de Informação) – Faculdade de Computação, Instituto de Ciências Exatas e Naturais, Universidade Federal do Pará, Belém. Disponível em: http://bdm.ufpa.br/jspui/handle/prefix/1434. Acesso em: 20-10-2024.
