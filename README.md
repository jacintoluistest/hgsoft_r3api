# hgsoft_r3api
REST API Testing through REST Assured

## RTR3S API Tests 
This repo allocates API test through Java and REST Assure framework to test APIs developed in R3 System.
This will be developed as PoC for presentation

### About REST Assured
Testing and validating REST services in Java is harder than in dynamic languages such as Ruby and Groovy. REST Assured brings the simplicity of using these languages into the Java domain. For example, if your HTTP server returns the following JSON at “http://localhost:8080/lotto/{id}”:

{
   "lotto":{
      "lottoId":5,
      "winning-numbers":[2,45,34,23,7,5,3],
      "winners":[
         {
            "winnerId":23,
            "numbers":[2,45,34,23,3,5]
         },
         {
            "winnerId":54,
            "numbers":[52,3,12,11,18,22]
         }
      ]
   }
}
You can easily use REST Assured to validate interesting things from the response:

@Test public void
lotto_resource_returns_200_with_expected_id_and_winners() {

    when().
            get("/lotto/{id}", 5).
    then().
            statusCode(200).
            body("lotto.lottoId", equalTo(5),
                 "lotto.winners.winnerId", hasItems(23, 54));

}

