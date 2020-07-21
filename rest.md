Условия REST:
1. Модель клиент-сервер. Система должна быть разделена на клиентов и на серверов.
2. Отсутствие состояния.  Сервер не должен хранить какой-либо информации о клиентах. В запросе должна храниться вся необходимая информация для обработки запроса и если необходимо, идентификации клиента
3. Кэширование. Ответы сервера должны иметь явное или неявное обозначение как кэшируемые или некэшируемые с целью предотвращения получения клиентами устаревших или неверных данных в ответ на последующие запросы
4. Единообразие интерфейса. Унифицированные интерфейсы позволяют каждому из сервисов развиваться независимо. 
5. Слои. Допускается разделить систему на иерархию слоев но с условием, что каждый компонент может видеть компоненты только непосредственно следующего слоя. Например, если вы вызывайте службу PayPal а он в свою очередь вызывает службу Visa, вы о вызове службы Visa ничего не должны знать.
6. Код по требованию (необязательное ограничение). В REST позволяется загрузка и выполнение кода или программы на стороне клиента.

-----------------------CLIENTS:-------------------------
1) Apache HttpCLient 
-GET:
  HttpClient client = new DefaultHttpClient();
  HttpGet request = new HttpGet('http://restUrl');
  HttpResponse response = client.execute(request);
  BufferedReader rd = new BufferedReader (new InputStreamReader(response.getEntity().getContent()));
  String line = '';
  while ((line = rd.readLine()) != null) {
  System.out.println(line);
  }
-POST:
  HttpClient client = new DefaultHttpClient();
  HttpPost post = new HttpPost('http://restUrl');
  StringEntity input = new StringEntity('product');
  post.setEntity(input);
  HttpResponse response = client.execute(post);
  BufferedReader rd = new BufferedReader(new InputStreamReader(response.getEntity().getContent()));
  String line = '';
  while ((line = rd.readLine()) != null) {
  System.out.println(line);
  }
--------------------------------------------------------
2) Jersey
-GET:
  ClientConfig config = new DefaultClientConfig();
  Client client = Client.create(config);
  WebResource service = client.resource(UriBuilder.fromUri('http://restUrl').build());
  // getting XML data
  System.out.println(service. path('restPath').path('resourcePath').accept(MediaType.APPLICATION_JSON).get(String.class));
  // getting JSON data
  System.out.println(service. path('restPath').path('resourcePath').accept(MediaType.APPLICATION_XML).get(String.class));
  }
-POST:
  ClientConfig config = new DefaultClientConfig();
  Client client = Client.create(config);
  WebResource webResource = client.resource(UriBuilder.fromUri('http://restUrl').build());
  MultivaluedMap formData = new MultivaluedMapImpl();
  formData.add('name1', 'val1');
  formData.add('name2', 'val2');
  ClientResponse response = webResource.type(MediaType.APPLICATION_FORM_URLENCODED_TYPE).post(ClientResponse.class, formData);
  System.out.println('Response ' + response.getEntity(String.class));
 }
--------------------------------------------------------
3) Java REST API
--------------------------------------------------------
4) Rest Template API
--------------------------------------------------------
