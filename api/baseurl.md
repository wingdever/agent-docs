# qiniu
https://portal.qiniu.com/ai-inference/api-key:

OpenAI BaseURL：
https://api.qnaigc.com/v1
Anthropic BaseURL：
https://api.qnaigc.com

# deepseek
base_url (OpenAI):	
https://api.deepseek.com
base_url (Anthropic):	
https://api.deepseek.com/anthropic
model:
deepseek-flash

```bash
curl https://api.deepseek.com/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer ${DEEPSEEK_API_KEY}" \
  -d '{
        "model": "deepseek-flash",
        "messages": [
          {"role": "system", "content": "You are a helpful assistant."},
          {"role": "user", "content": "Hello!"}
        ],
        "thinking": {"type": "enabled"},
        "reasoning_effort": "high",
        "stream": false
      }'
```

https://api.deepseek.com/chat/completions
