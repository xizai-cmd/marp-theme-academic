---
marp: true
theme: academic
paginate: true
math: katex
---

<!-- _class: lead -->

# 用 Marp 制作研究室汇报幻灯片

#### ～告别 Beamer～

<br>

**作者 太郎**
某某研究室 M2
YYYY/MM/DD

---

<!-- _header: 目录 -->

1. 简介
1. 内容块
1. 代码块
1. 数学公式
1. 表格
1. 图片

---

<!-- _header: 简介 -->

- Marp 是一款用 **Markdown** 制作**幻灯片**的软件。
  - 支持基本的 Markdown 语法。
- 在 Markdown 中只需插入 `---` 这样的分隔线，就能切换到下一页。

---

<!-- _header: 内容块 -->

> ###### 定义
>
> 把引用块的第一行写成六级标题 `######`，就会生成像这样的标题栏。

> 第一行不是六级标题时，就是一个没有标题栏的内容块。

---

<!-- _header: 代码块 -->

```python
import torch
print(torch.cuda.is_available())
```

像这样就能编写代码块。

```python
from transformers import AutoModelForMaskedLM, AutoTokenizer
model = AutoModelForMaskedLM.from_pretrained("cl-tohoku/bert-base-japanese-whole-word-masking")
tokenizer = AutoTokenizer.from_pretrained("cl-tohoku/bert-base-japanese-whole-word-masking")

inputs = tokenizer.encode_plus("私はとても[MASK]です。", return_tensors='pt')
outputs = model(**inputs)
tokenizer.convert_ids_to_tokens(outputs.logits[0][1:-1].argmax(axis=-1))
```

宽度会自动调整（参见文档的 [Auto-scaling](https://github.com/marp-team/marp-core#auto-scaling-features)）。

---

<!-- _header: 数学公式 -->

$$ I_{xx}=\int\int_Ry^2f(x,y)\cdot{}dydx $$

$$
f(x) = \int_{-\infty}^\infty
    \hat f(\xi)\,e^{2 \pi i \xi x}
    \,d\xi
$$

像这样就能编写数学公式。当然也可以使用行内的 $\LaTeX$。  
顺便一提，还能使用 emoji:smile:

---

<!-- _header: 表格 -->

| 方法 | 参数量 | 准确率 | 备注 |
| :--- | ---: | :---: | :--- |
| Baseline | 110M | 88.4% | 复现结果 |
| Ours | 118M | **91.2%** | $p < 0.01$ |
| Ours (large) | 340M | 92.0% | `batch=64` |

像这样就能编写表格。

---

<!-- _header: 图片 -->

1. 首先从[这个 Irasutoya 链接](https://www.irasutoya.com/2018/10/blog-post_723.html)右键下载图片（`kenkyu_woman_seikou.png`）。
2. 在此 Markdown 文件所在的目录中新建一个名为 `images` 的目录，并把刚才下载的图片放进去。这样准备工作就完成了。

![w:300 center](./images/kenkyu_woman_seikou.png)
