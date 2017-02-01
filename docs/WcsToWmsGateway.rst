WcsToWmsGateway Service
=======================================

Serviço responsável por receber as mensagens do WCS KNAPP e 
enviar para o WMS HighJump

Configuração
-----------------------
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

Localização do executável no servidor de aplicação::

    C:\Servicos\WcsToWmsGateway

Parâmetros disponíveis no **App.config**:

+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| Parâmetro                                          | Descrição                                                                           | Valor Default                                                                                              |
+====================================================+=====================================================================================+============================================================================================================+
| ``connectionString/Default``                       | String de conexão com banco de dados                                                | ``Data Source=SERVIDOR DB;Initial Catalog=AAD;Persist Security Info=True;User ID=USUARIO;Password=SENHA;`` |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| ``appSettings/WCS-IP``                             | Endereço IP do servidor KNAPP                                                       | ``10.85.243.1``                                                                                            |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| ``appSettings/WCS-PORT``                           | Porta TCP/IP que a KNAPP envia as mensagens                                         | ``9802``                                                                                                   |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
| ``appSettings/SLEEP-VERIFICAR-SERVICO-HABILITADO`` | Tempo, em segundos, de espera para verificar novamente se o serviço está habilitado | ``10000``                                                                                                  |
+----------------------------------------------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

Instalação/Desintalação
-----------------------
Instalar::

    C:\Servicos\WcsToWmsGateway\WcsToWmsGateway.exe install

Desinstalar::

    C:\Servicos\WcsToWmsGateway\WcsToWmsGateway.exe uninstall


.. note::
    Abra o prompt como ADMINISTRADOR

Execução
-----------------------
Start::

    C:\Servicos\WcsToWmsGateway\WcsToWmsGateway.exe start

Stop::

    C:\Servicos\WcsToWmsGateway\WcsToWmsGateway.exe stop

.. note::
    Abra o prompt como ADMINISTRADOR

Monitoramento
-----------------------
Toda troca de mensagens é registrada em arquivo texto de log.

Localização do log em arquivo texto::

    C:\Servicos\WcsToWmsGateway\logs\YYYY-MM-DD.log

É possível visualizar o log em tempo real por meio do `Sentiel`_ Viewer:

    1. Abra o Sentinel e crie uma nova session
    2. Escolha o provider ``NLog Viewer Provider``
    3. Em seguida o protocolo ``UDP`` e porta ``9998``


.. _Sentiel: http://sentinel.codeplex.com/