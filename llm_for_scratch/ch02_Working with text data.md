
# Tokenizing text

## Q1. 正则表达式


# Converting tokens into token IDs

- step1. 构建词汇表（建立每个词和ID的一一对应关系）
	- encode： text --> IDs, decode: IDs --> text

# Adding special context tokens
处理词汇表中未出现的单词，以及特殊符号（开始<|startoftext|>、结束<|endoftext|>、未知<|unk|>等）

# Byte pair encoding
把未知的词语可以分成已知的子词
`（需要自己看下GPT-2的实现）`

BPE每一步将最常见的一对相邻数据单位替换为该数据中没有出现过的一个新单位，反复迭代直到满足条件为止

构造词表时会把每个sub-word都放在词表内，分词时就在词表里面尝试找到最长的sub-word

# Data sampling with a sliding window

next word prediction?

# Creating token embeddings

将input_token_ids转换为embedding
```python
torch.nn.linear
torch.nn.embeddings
# 有什么区别？？？
```
苏剑林博客：有的只是one-hot，并没有embedding

embedding输入的是整数tensor，执行的是索引操作，没有偏置

# Encoding word positions

RoPE（需了解）：“绝对位置编码的方式实现相对位置编码”
bolg链接[Rope](https://www.spaces.ac.cn/archives/8265/comment-page-1)


GPT-2中把位置信息过另一个embedding layer加到input_token embedding