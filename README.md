# callAPI-android-studio

### Créer une Class

```java
public class HttpUtils {
  private static final String BASE_URL = "http://url_basic_de_mon_api/";

  private static AsyncHttpClient client = new AsyncHttpClient();

  public static void get(String url, RequestParams params, AsyncHttpResponseHandler responseHandler) {
      client.get(getAbsoluteUrl(url), params, responseHandler);
  }

  public static void post(String url, RequestParams params, AsyncHttpResponseHandler responseHandler) {
      client.post(getAbsoluteUrl(url), params, responseHandler);
  }

  public static void getByUrl(String url, RequestParams params, AsyncHttpResponseHandler responseHandler) {
      client.get(url, params, responseHandler);
  }

  public static void postByUrl(String url, RequestParams params, AsyncHttpResponseHandler responseHandler) {
      client.post(url, params, responseHandler);
  }

  private static String getAbsoluteUrl(String relativeUrl) {
      return BASE_URL + relativeUrl;
  }
}
```

### Exemple de Méthode d'appel

```java
  RequestParams rp = new RequestParams();
    rp.add("username", "nom_utilisateur"); rp.add("password", "S3cr3t@123");

    HttpUtils.post(AppConstant.URL_FEED, rp, new JsonHttpResponseHandler() {
        @Override
        public void onSuccess(int statusCode, Header[] headers, JSONObject response) {
            // Si la réponse est Object JSON au lieu d'un Array JSON, attendu
            Log.d("asd", "---------------- this is response : " + response);
            try {
                JSONObject serverResp = new JSONObject(response.toString());                                                
            } catch (JSONException e) {
                e.printStackTrace();
            }                   
        }

        @Override
        public void onSuccess(int statusCode, Header[] headers, JSONArray timeline) {
        }
    });
```

#### NB :

`Log.e :` C'est pour quand de mauvaises choses se produisent. Utilisez cette balise à des endroits comme dans une déclaration catch. Vous savez qu'une erreur s'est produite et vous enregistrez donc une erreur.

`Log.w :` utilisez-le lorsque vous soupçonnez que quelque chose de louche se passe. Vous n'êtes peut-être pas complètement en mode d'erreur, mais vous avez peut-être récupéré d'un comportement inattendu. Fondamentalement, utilisez-le pour enregistrer des choses que vous ne vous attendiez pas, mais ce n'est pas nécessairement une erreur. Un peu comme un "hé, c'est arrivé, et c'est bizarre , on devrait y regarder."

`Log.i :` utilisez-le pour publier des informations utilesdans le journal. Par exemple: que vous vous êtes connecté avec succès à un serveur. Fondamentalement, utilisez-le pour signaler les succès.

`Log.d :` utilisez-le à des fins de débogage . Si vous souhaitez imprimer un tas de messages afin de pouvoir enregistrer le flux exact de votre programme, utilisez ceci. Si vous souhaitez conserver un journal des valeurs des variables, utilisez-le.

`Log.v :` utilisez-le lorsque vous voulez devenir complètement fou avec votre journalisation. Si, pour une raison quelconque, vous avez décidé d'enregistrer chaque petite chose dans une partie particulière de votre application, utilisez la balise Log.v.

`Log.wtf :` utilisez-le lorsque les choses se passent de manière absolument horrible, merde. Vous connaissez ces blocs catch où vous attrapez des erreurs que vous ne devriez jamais obtenir ... oui, si vous voulez les enregistrer, utilisez Log.wtf
