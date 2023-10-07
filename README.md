# Python HTTP Function

This is a simple HTTP function written in Python that can be deployed to Google Cloud Functions. The function responds to HTTP requests with a "Hello, World!" message.

## Deployment

To deploy the function to Google Cloud Functions, you can use the following command:

```
gcloud functions deploy python-http-function \
  --gen2 \
  --runtime=python311 \
  --region=asia-southeast1 \
  --source=. \
  --entry-point=hello_http \
  --trigger-http \
  --allow-unauthenticated
```

Make sure to replace `python-http-function` with the name of your function, and adjust the region and other parameters as needed.

## Usage

Once the function is deployed, you can send HTTP requests to its URL to trigger it. The function will respond with a "Hello, World!" message.

To trigger the function using a POST request, you can use the following `curl` command:

```
curl -X POST \
  -H "Content-Type: application/json" \
  -d '{"name": "Nutty"}' \
  https://<YOUR_FUNCTION_URL>
```

Make sure to replace `<YOUR_FUNCTION_URL>` with the URL of your deployed function. This `curl` command sends a POST request to the function with a JSON payload containing a `name` field set to `"Nutty"`. The `-H` option sets the `Content-Type` header to `application/json`, and the `-d` option specifies the data to send in the request body.

To trigger the function using a GET request, you can simply navigate to the URL of your deployed function in a web browser or use the following `curl` command:

```
curl https://<YOUR_FUNCTION_URL>?name=Nutty
```

Make sure to replace `<YOUR_FUNCTION_URL>` with the URL of your deployed function. This `curl` command sends a GET request to the function with a query parameter `name` set to `"Nutty"`. The function will extract the value of the `name` parameter from the request and respond with a message that includes the value of the `name` variable.