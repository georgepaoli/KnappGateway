WmsToWcsGateway Service
=======================================

Serviço responsável por receber as mensagens do WMS HighJump e 
enviar para o WCS KNAPP

Fluxo
-----------------------
.. image:: /img/fluxo-wms-to-wcs.png

Configuração
-----------------------
Requisitos mínimos:

    * Windows Server 2012 R2 - 64bit
    * .NET Framework v4.6
    * 4GB de RAM
    * Intel Xeon 2.60GHz

Ambientes e Servidores:

+-------------------------------------+-----------------------+-------------------+
| Servidor/IP                         | Função                | Ambiente          |
+=====================================+=======================+===================+
| ``WINPKNAPPGW``                     | Servidor de Aplicação | ``PRODUCAO``      |
+-------------------------------------+-----------------------+-------------------+
| ``WINDHTKNAPPGW``                   | Servidor de Aplicação | ``HOMOLOGACAÇÃO`` |
+-------------------------------------+-----------------------+-------------------+
| ``???\HCDNHJS``                     | Servidor de Banco     | ``PRODUCAO``      |
+-------------------------------------+-----------------------+-------------------+
| ``WINDHTSQLCDN02\HCDNHJS``          | Servidor de Banco     | ``HOMOLOGACAÇÃO`` |
+-------------------------------------+-----------------------+-------------------+

Localização dos arquivos no servidor de aplicação::

    C:\Servicos\WmsToWcsGateway

Parâmetros disponíveis no **App.config**:

+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| Parâmetro                                          | Descrição                                                                           | Valor Default                                                                                              |
+====================================================+=====================================================================================+============================================================================================================+
| ``connectionString/Default``                       | String de conexão com banco de dados                                                | ``Data Source=SERVIDOR DB;Initial Catalog=AAD;Persist Security Info=True;User ID=USUARIO;Password=SENHA;`` |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| ``appSettings/WCS-IP``                             | Endereço IP do servidor KNAPP                                                       | ``10.85.243.1``                                                                                            |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| ``appSettings/WCS-PORT``                           | Porta TCP/IP que a KNAPP recebe as mensagens do WMS                                 | ``9801``                                                                                                   |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| ``appSettings/SLEEP-VERIFICAR-SERVICO-HABILITADO`` | Tempo, em segundos, de espera para verificar novamente se o serviço está habilitado | ``10000``                                                                                                  |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| ``appSettings/SLEEP-VERIFICAR-NOVA-MENSAGEM``      | Tempo, em segundos, de espera para verificar se existe uma nova mensagem            | ``10000``                                                                                                  |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

.. note::
    É necessário efetuar o stop e start do serviço após qualquer ajuste nas configurações

Instalação/Desintalação
-----------------------
Instalar::

    C:\Servicos\WmsToWcsGateway\WmsToWcsGateway.exe install

Desinstalar::

    C:\Servicos\WmsToWcsGateway\WmsToWcsGateway.exe uninstall


.. note::
    Execute o prompt como ADMINISTRADOR

Execução
-----------------------
.. warning:: 
    **IMPORTANTE**: Antes de iniciar o serviço, é necessário desligar a interface do WMS Hight Jump, caso esteja ligada.
    
Start::

    C:\Servicos\WmsToWcsGateway\WmsToWcsGateway.exe start

Stop::

    C:\Servicos\WmsToWcsGateway\WmsToWcsGateway.exe stop

.. note::
    Execute o prompt como ADMINISTRADOR

Monitoramento
-----------------------
Toda troca de mensagens é registrada em arquivo texto de log.

Localização do log em arquivo texto::

    C:\Servicos\WmsToWcsGateway\logs\YYYY-MM-DD.log

É possível visualizar o log em tempo real por meio do `Sentiel`_ Viewer:

    1. Abra o Sentinel e crie uma nova session
    2. Escolha o provider ``NLog Viewer Provider``
    3. Em seguida o protocolo ``UDP`` e porta ``9999``

.. note::
    1. Detalhes de configuração do mecanismo de log estão localizados no arquivo NLog.config. Após qualquer ajuste é necessário efetuar o stop e start do serviço
    2. Limpeza do log: Arquivos com mais de uma semana, serão excluídos


.. _Sentiel: http://sentinel.codeplex.com/