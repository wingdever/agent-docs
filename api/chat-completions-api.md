# Request
--data '{...}'

## data
"model": "deepseek-flash",
"messages": [...],
"max_tokens": 32,
"temperature": 0,
"thinking": { "type": "disabled" },
"stream": false

## messages
enum role: [system,user,assistant,tool] 
struct system_prompt {
    content string required
    role "system"
    name string optional -- different participant
}
struct user_input {
    content string required
    role "user"
    name string optional
}
struct assistant_reply {
    content string required
    role "assistant"
    name string optional
}
struct tool_result {
    role "tool"
    content string required
    tool_call_id string required
}

## required_para
enum model: [deepseek-flash,deepseek-v4-pro]

## nullable_para
### thinking and reasoning_effort
struct thinking {
    type string required
} 
enum type: [enabled,disabled]
enum reasoning_effort string: [none,low,high,max] default high

if all null then default thinking mode enable
if thinking provide, as it for gate
else as reasoning_effort for level
### max_tokens
### response_format
struct response_format {
    type string required
}
enum type string: [text,json_object] default text
### stop
### stream
boolean stream default false
### temperature and top_p
number temperature [0,2] default 1
number top_p (0),[1]  
### tools
list tools [{
    type "function"
    function object required
}]
struct function {
    description string required
    name string required unique
    parameters object nullable
    strict boolean nullable default false
}
struct parameters {
    ...
}

### tool_choice string|object
enum tool_choice string: [none,auto,required]
struct tool_choice {
    type "function"
    function object required
}
struct function {
    name string required
}

string: 
    none: not call any tool.
    auto: pick between generating message or calling tools.
    required: must call one or more tools.
object: force the model to call a specific function


### logprobs and top_logprobs
boolean logprobs default false
integer top_logprobs in [0,20] default null

### user_id
for content-safety-review
for KVCache-isolation for privacy-management
for scheduling-isolation on bussiness-side



# Response
## Response-Not-streaming
struct chat_completion_object {
    id string required
    choices array required
    created integer required
    model string required
    system_fingerprint string required
    object "chat.completion"
    usage object
}
### choices
list choices [{
    finish_reason string required
    index integer ? required
    message object required
    logprobs object nullable
}]
enum finish_reason: [
    stop,
    length,
    content_filter,
    tool_calls,
    insufficient_system_resource,
    aborted
]
#### message
struct message {
    content string
    reasoning_content string nullable
    tool_calls array
    role "assistant"
}
list tool_calls [{
    id string required
    type "func"
    function object
}]
struct function {
    name string required
    arguments string requied
}

### usage
struct usage {
    completion_tokens integer
    prompt_tokens integer
    prompt_tokens_details object
    prompt_cache_hit_tokens integer
    prompt_cache_miss_tokens integer
    total_tokens integer
    completion_tokens_details object
}
struct prompt_tokens_details {
    cached_tokens integer
}
struct completion_tokens_details {
    reasoning_tokens integer
}

## Response-Streaming
struct chat_completion_object {
    id string required
    choices array required
    created integer required
    model string required
    system_fingerprint string required
    object "chat.completion.chunk"
    usage object
}

### choices
list choices [{
    delta object required
    finish_reason string required
    index integer ? required
    message object required
    logprobs object nullable
}]

struct delta {
    content string required
}
