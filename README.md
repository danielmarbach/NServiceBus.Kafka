Kafka transport for NServiceBus. Part of:
https://pablocastilla.wordpress.com/2017/01/03/my-proposal-for-joining-net-and-the-hadoop-ecosystem/

Example of configuring the consumer:
            
            endpointConfiguration.UseTransport<KafkaTransport>().ConnectionString("127.0.0.1:9092");
 
                
                
Example of configuring the sender:

       static async Task<IEndpointInstance> GetInstance()
        {
            var endpointConfiguration = new EndpointConfiguration("EndpointName");
            endpointConfiguration.UseTransport<KafkaTransport>().ConnectionString("127.0.0.1:9092"); ;
            endpointConfiguration.SendOnly();
            return await Endpoint.Start(endpointConfiguration)
                .ConfigureAwait(false);
        }
