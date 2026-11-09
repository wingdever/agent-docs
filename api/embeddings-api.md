post https://maas-api.cn-huabei-1.xf-yun.com/v2/embeddings

request-parameter:
model string model_id required
input string/array text or [text,,] required
encoding_format float nullable
dimensions int nullable

response:
id string
object string usually "list"
created int
model string
data array object
    index int
    object string usually "embedding"
    embedding array float
usage object
    prompt_tokens int
    total_tokens int
