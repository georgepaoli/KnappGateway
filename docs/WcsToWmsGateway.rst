WcsToWmsGateway
=======================================

Serviço responsável por receber as mensagens do WCS KNAPP e 
enviar para o WMS HighJump

Configuração
-----------------------
Ambientes e Servidores:

+-------------------------------------+-----------------------+-------------------+
| Servidor                            | Função                | Ambiente          |
+=====================================+=======================+===================+
| ``WINPKNAPPGW``                     | Servidor de Aplicação | ``PRODUCAO``      |
+-------------------------------------+-----------------------+-------------------+
| ``WINDHTKNAPPGW``                   | Servidor de Aplicação | ``HOMOLOGACAÇÃO`` |
+-------------------------------------+-----------------------+-------------------+
| ``WINDHTSQLCDN02\HCDNHJS``          | Servidor de Banco     | ``HOMOLOGACAÇÃO`` |
+-------------------------------------+-----------------------+-------------------+

Localização do executável no servidor::

    C:\Servicos\WcsToWmsGateway

App.config:

.. code-block:: xml

    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
        </startup>
        <connectionStrings>
            <clear />
            <!-- String de conexão com o banco da HighJump -->
            <add name="Default" 
                connectionString="Data Source=WINDHTSQLCDN02\HCDNHJS;Initial Catalog=AAD;Persist Security Info=True;User ID=HJS;Password=HJSPASS#1;" 
                providerName="System.Data.SqlClient" />
        </connectionStrings>
        <appSettings>
            <!-- Endereço IP do servidor da KNAPP -->
            <add key="WCS-IP" value="10.85.243.1"/>
            
            <!-- Porta TCP/IP quea KNAPP envia as mensagens -->
            <add key="WCS-PORT" value="9802"/>
            
            <!-- Tempo, em segundos, de espera para verificar novamente se o serviço está habilitado -->
            <add key="SLEEP-VERIFICAR-SERVICO-HABILITADO" value="10000"/>
        </appSettings>
    </configuration>

Instalação
-----------------------


Execução
-----------------------
Monitoramento
-----------------------