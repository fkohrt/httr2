# req has basic print method

    Code
      req <- request("https://example.com")
      req
    Message <cliMessage>
      <httr2_request>
      GET https://example.com
      Body: empty
    Code
      req %>% req_body_raw("Test")
    Message <cliMessage>
      <httr2_request>
      POST https://example.com
      Body: a string
    Code
      req %>% req_body_multipart(list(Test = 1))
    Message <cliMessage>
      <httr2_request>
      POST https://example.com
      Body: multipart encoded data

# individually prints repeated headers

    Code
      request("https://example.com") %>% req_headers(A = 1:3)
    Message <cliMessage>
      <httr2_request>
      GET https://example.com
      Headers:
      * A: '1'
      * A: '2'
      * A: '3'
      Body: empty

# check_request() gives useful error

    Code
      check_request(1)
    Error <rlang_error>
      `req` must be an HTTP request object
