# [824. 山羊拉丁文](https://leetcode.cn/problems/goat-latin)

[English Version](/solution/0800-0899/0824.Goat%20Latin/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给定一个由空格分割单词的句子&nbsp;<code>S</code>。每个单词只包含大写或小写字母。</p>

<p>我们要将句子转换为&nbsp;<em>&ldquo;Goat Latin&rdquo;</em>（一种类似于 猪拉丁文&nbsp;- Pig Latin 的虚构语言）。</p>

<p>山羊拉丁文的规则如下：</p>

<ul>
	<li>如果单词以元音开头（a, e, i, o, u），在单词后添加<code>&quot;ma&quot;</code>。<br />
	例如，单词<code>&quot;apple&quot;</code>变为<code>&quot;applema&quot;</code>。</li>
	<br />
	<li>如果单词以辅音字母开头（即非元音字母），移除第一个字符并将它放到末尾，之后再添加<code>&quot;ma&quot;</code>。<br />
	例如，单词<code>&quot;goat&quot;</code>变为<code>&quot;oatgma&quot;</code>。</li>
	<br />
	<li>根据单词在句子中的索引，在单词最后添加与索引相同数量的字母<code>&#39;a&#39;</code>，索引从1开始。<br />
	例如，在第一个单词后添加<code>&quot;a&quot;</code>，在第二个单词后添加<code>&quot;aa&quot;</code>，以此类推。</li>
</ul>

<p>返回将&nbsp;<code>S</code>&nbsp;转换为山羊拉丁文后的句子。</p>

<p><strong>示例 1:</strong></p>

<pre>
<strong>输入: </strong>&quot;I speak Goat Latin&quot;
<strong>输出: </strong>&quot;Imaa peaksmaaa oatGmaaaa atinLmaaaaa&quot;
</pre>

<p><strong>示例 2:</strong></p>

<pre>
<strong>输入: </strong>&quot;The quick brown fox jumped over the lazy dog&quot;
<strong>输出: </strong>&quot;heTmaa uickqmaaa rownbmaaaa oxfmaaaaa umpedjmaaaaaa overmaaaaaaa hetmaaaaaaaa azylmaaaaaaaaa ogdmaaaaaaaaaa&quot;
</pre>

<p><strong>说明:</strong></p>

<ul>
	<li><code>S</code>&nbsp;中仅包含大小写字母和空格。单词间有且仅有一个空格。</li>
	<li><code>1 &lt;= S.length &lt;= 150</code>。</li>
</ul>

## 解法

<!-- 这里可写通用的实现逻辑 -->

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def toGoatLatin(self, sentence: str) -> str:
        ans = []
        for i, word in enumerate(sentence.split()):
            if word.lower()[0] not in ['a', 'e', 'i', 'o', 'u']:
                word = word[1:] + word[0]
            word += 'ma'
            word += 'a' * (i + 1)
            ans.append(word)
        return ' '.join(ans)
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public String toGoatLatin(String sentence) {
        List<String> ans = new ArrayList<>();
        Set<Character> vowels = new HashSet<>(Arrays.asList('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'));
        int i = 1;
        for (String word : sentence.split(" ")) {
            StringBuilder t = new StringBuilder();
            if (!vowels.contains(word.charAt(0))) {
                t.append(word.substring(1));
                t.append(word.charAt(0));
            } else {
                t.append(word);
            }
            t.append("ma");
            for (int j = 0; j < i; ++j) {
                t.append("a");
            }
            ++i;
            ans.add(t.toString());
        }
        return String.join(" ", ans);
    }
}
```

### **TypeScript**

```ts
function toGoatLatin(sentence: string): string {
    return sentence
        .split(' ')
        .map((s, i) => {
            let startStr: string;
            if (/[aeiou]/i.test(s[0])) {
                startStr = s;
            } else {
                startStr = s.slice(1) + s[0];
            }
            return `${startStr}ma${'a'.repeat(i + 1)}`;
        })
        .join(' ');
}
```

### **Rust**

```rust
use std::collections::HashSet;
impl Solution {
    pub fn to_goat_latin(sentence: String) -> String {
        let set: HashSet<&char> = ['a', 'e', 'i', 'o', 'u'].into_iter().collect();
        sentence
            .split_whitespace()
            .enumerate()
            .map(|(i, s)| {
                let first = char::from(s.as_bytes()[0]);
                let mut res = if set.contains(&first.to_ascii_lowercase()) {
                    s.to_string()
                } else {
                    s[1..].to_string() + &first.to_string()
                };
                res.push_str("ma");
                res.push_str(&"a".repeat(i + 1));
                res
            })
            .into_iter()
            .collect::<Vec<String>>()
            .join(" ")
    }
}
```

### **...**

```

```

<!-- tabs:end -->
