<!--
AUTHORS:
Prefer only GitHub-flavored Markdown in external text.
See README.md for details.
-->

# Google Python Style Guide

<!-- markdown="1" is required for GitHub Pages to render the TOC properly. -->

<details markdown="1">
  <summary>Table of Contents</summary>

- [Google Python Style Guide](#google-python-style-guide)
  - [1 Background (背景)](#1-background-背景)
  - [2 Python Language Rules](#2-python-language-rules)
    - [2.1 Lint](#21-lint)
      - [2.1.1 Definition](#211-definition)
      - [2.1.2 Pros](#212-pros)
      - [2.1.3 Cons](#213-cons)
      - [2.1.4 Decision](#214-decision)
    - [2.2 Imports](#22-imports)
      - [2.2.1 Definition](#221-definition)
      - [2.2.2 Pros](#222-pros)
      - [2.2.3 Cons](#223-cons)
      - [2.2.4 Decision](#224-decision)
    - [2.3 Packages](#23-packages)
      - [2.3.1 Pros](#231-pros)
      - [2.3.2 Cons](#232-cons)
      - [2.3.3 Decision](#233-decision)
    - [2.4 Exceptions](#24-exceptions)
      - [2.4.1 Definition](#241-definition)
      - [2.4.2 Pros](#242-pros)
      - [2.4.3 Cons](#243-cons)
      - [2.4.4 Decision](#244-decision)
    - [2.5 Global variables](#25-global-variables)
      - [2.5.1 Definition](#251-definition)
      - [2.5.2 Pros](#252-pros)
      - [2.5.3 Cons](#253-cons)
      - [2.5.4 Decision](#254-decision)
    - [2.6 Nested/Local/Inner Classes and Functions](#26-nestedlocalinner-classes-and-functions)
      - [2.6.1 Definition](#261-definition)
      - [2.6.2 Pros](#262-pros)
      - [2.6.3 Cons](#263-cons)
      - [2.6.4 Decision](#264-decision)
    - [2.7 Comprehensions & Generator Expressions](#27-comprehensions--generator-expressions)
      - [2.7.1 Definition](#271-definition)
      - [2.7.2 Pros](#272-pros)
      - [2.7.3 Cons](#273-cons)
      - [2.7.4 Decision](#274-decision)
    - [2.8 Default Iterators and Operators](#28-default-iterators-and-operators)
      - [2.8.1 Definition](#281-definition)
      - [2.8.2 Pros](#282-pros)
      - [2.8.3 Cons](#283-cons)
      - [2.8.4 Decision](#284-decision)
    - [2.9 Generators](#29-generators)
      - [2.9 Definition](#29-definition)
      - [2.9.2 Pros](#292-pros)
      - [2.9.3 Cons](#293-cons)
      - [2.9.4 Decision](#294-decision)
    - [2.10 Lambda Functions](#210-lambda-functions)
      - [2.10.1 Definition](#2101-definition)
      - [2.10.2 Pros](#2102-pros)
      - [2.10.3 Cons](#2103-cons)
      - [2.10.4 Decision](#2104-decision)
    - [2.11 Conditional Expressions](#211-conditional-expressions)
      - [2.11.1 Definition](#2111-definition)
      - [2.11.2 Pros](#2112-pros)
      - [2.11.3 Cons](#2113-cons)
      - [2.11.4 Decision](#2114-decision)
    - [2.12 Default Argument Values](#212-default-argument-values)
      - [2.12.1 Definition](#2121-definition)
      - [2.12.2 Pros](#2122-pros)
      - [2.12.3 Cons](#2123-cons)
      - [2.12.4 Decision](#2124-decision)
    - [2.13 Properties](#213-properties)
      - [2.13.1 Definition](#2131-definition)
      - [2.13.2 Pros](#2132-pros)
      - [2.13.3 Cons](#2133-cons)
      - [2.13.4 Decision](#2134-decision)
    - [2.14 True/False Evaluations](#214-truefalse-evaluations)
      - [2.14.1 Definition](#2141-definition)
      - [2.14.2 Pros](#2142-pros)
      - [2.14.3 Cons](#2143-cons)
      - [2.14.4 Decision](#2144-decision)
    - [2.16 Lexical Scoping](#216-lexical-scoping)
      - [2.16.1 Definition](#2161-definition)
      - [2.16.2 Pros](#2162-pros)
      - [2.16.3 Cons](#2163-cons)
      - [2.16.4 Decision](#2164-decision)
    - [2.17 Function and Method Decorators](#217-function-and-method-decorators)
      - [2.17.1 Definition](#2171-definition)
      - [2.17.2 Pros](#2172-pros)
      - [2.17.3 Cons](#2173-cons)
      - [2.17.4 Decision](#2174-decision)
    - [2.18 Threading](#218-threading)
    - [2.19 Power Features](#219-power-features)
      - [2.19.1 Definition](#2191-definition)
      - [2.19.2 Pros](#2192-pros)
      - [2.19.3 Cons](#2193-cons)
      - [2.19.4 Decision](#2194-decision)
    - [2.20 Modern Python: Python 3 and from \_\_future\_\_ imports](#220-modern-python-python-3-and-from-__future__-imports)
      - [2.20.1 Definition](#2201-definition)
      - [2.20.2 Pros](#2202-pros)
      - [2.20.3 Cons](#2203-cons)
      - [2.20.4 Decision](#2204-decision)
        - [from \_\_future\_\_ imports](#from-__future__-imports)
        - [The six, future, and past libraries](#the-six-future-and-past-libraries)
    - [2.21 Type Annotated Code](#221-type-annotated-code)
      - [2.21.1 Definition](#2211-definition)
      - [2.21.2 Pros](#2212-pros)
      - [2.21.3 Cons](#2213-cons)
      - [2.21.4 Decision](#2214-decision)
  - [3 Python Style Rules](#3-python-style-rules)
    - [3.1 Semicolons](#31-semicolons)
    - [3.2 Line length](#32-line-length)
    - [3.3 Parentheses (カッコ)](#33-parentheses-カッコ)
    - [3.4 Indentation (インデント)](#34-indentation-インデント)
    - [3.4.1 Trailing commas in sequences of items? (アイテムのシーケンスの末尾のコンマ？)](#341-trailing-commas-in-sequences-of-items-アイテムのシーケンスの末尾のコンマ)
    - [3.5 Blank Lines (空白行)](#35-blank-lines-空白行)
    - [3.6 Whitespace (空白)](#36-whitespace-空白)
    - [3.7 Shebang Line](#37-shebang-line)
    - [3.8 Comments and Docstrings](#38-comments-and-docstrings)
      - [3.8.1 Docstrings](#381-docstrings)
      - [3.8.2 Modules](#382-modules)
      - [3.8.3 Functions and Methods](#383-functions-and-methods)
      - [3.8.4 Classes](#384-classes)
      - [3.8.5 Block and Inline Comments](#385-block-and-inline-comments)
      - [3.8.6 Punctuation, Spelling, and Grammar](#386-punctuation-spelling-and-grammar)
    - [3.10 Strings](#310-strings)
      - [3.10.1 Logging](#3101-logging)
      - [3.10.2 Error Messages](#3102-error-messages)
    - [3.11 Files and Sockets](#311-files-and-sockets)
    - [3.12 TODO Comments](#312-todo-comments)
    - [3.13 Imports formatting](#313-imports-formatting)
    - [3.14 Statements](#314-statements)
    - [3.15 Accessors](#315-accessors)
    - [3.16 Naming](#316-naming)
      - [3.16.1 Names to Avoid (避けるべき名前)](#3161-names-to-avoid-避けるべき名前)
      - [3.16.2 Naming Conventions (命名規則)](#3162-naming-conventions-命名規則)
      - [3.16.3 File Naming (ファイルの命名)](#3163-file-naming-ファイルの命名)
      - [3.16.4 Guidelines derived from Guido's Recommendations](#3164-guidelines-derived-from-guidos-recommendations)
    - [3.17 Main](#317-main)
    - [3.18 Function length (関数の長さ)](#318-function-length-関数の長さ)
    - [3.19 Type Annotations (タイプ注釈)](#319-type-annotations-タイプ注釈)
      - [3.19.1 General Rules (一般的なルール)](#3191-general-rules-一般的なルール)
      - [3.19.2 Line Breaking (改行)](#3192-line-breaking-改行)
      - [3.19.3 Forward Declarations (前方宣言)](#3193-forward-declarations-前方宣言)
      - [3.19.4 Default Values (デフォルト値)](#3194-default-values-デフォルト値)
      - [3.19.5 NoneType](#3195-nonetype)
      - [3.19.6 Type Aliases](#3196-type-aliases)
      - [3.19.7 Ignoring Types (タイプを無視する)](#3197-ignoring-types-タイプを無視する)
      - [3.19.8 Typing Variables (変数の入力)](#3198-typing-variables-変数の入力)
      - [3.19.9 Tuples vs Lists (タプルとリスト)](#3199-tuples-vs-lists-タプルとリスト)
      - [3.19.10 TypeVars](#31910-typevars)
      - [3.19.11 String types (文字列タイプ)](#31911-string-types-文字列タイプ)
      - [3.19.12 Imports For Typing](#31912-imports-for-typing)
      - [3.19.13 Conditional Imports (条件付きインポート)](#31913-conditional-imports-条件付きインポート)
      - [3.19.14 Circular Dependencies (循環依存)](#31914-circular-dependencies-循環依存)
      - [3.19.15 Generics](#31915-generics)
  - [4 Parting Words](#4-parting-words)

</details>

<a id="s1-background"></a>
<a id="1-background"></a>

<a id="background"></a>

## 1 Background (背景)

Pythonは、Googleで使用される主要な動的言語です。
このスタイルガイドは、Pythonプログラムの *推奨事項と禁止事項* のリストです。

コードを正しくフォーマットできるように、[Vimの設定ファイル](google_python_style.vim)を作成しました。
Emacsの場合、デフォルト設定で問題ありません。

多くのチームは、[yapf](https://github.com/google/yapf/) オートフォーマッターを使用して、フォーマットについての議論を避けています。

<a id="s2-python-language-rules"></a>
<a id="2-python-language-rules"></a>

<a id="python-language-rules"></a>

## 2 Python Language Rules

<a id="s2.1-lint"></a>
<a id="21-lint"></a>

<a id="lint"></a>

### 2.1 Lint

この [pylintrc](https://google.github.io/styleguide/pylintrc) を使用して、
コードに対して `pylint` を実行します。

<a id="s2.1.1-definition"></a>
<a id="211-definition"></a>

<a id="lint-definition"></a>

#### 2.1.1 Definition

`pylint` は、Pythonソースコードのバグやスタイルの問題を見つけるためのツールです。
これは、CやC++などの動的でない言語のコンパイラーによって通常キャッチされる問題を検出します。
Pythonの動的な性質により、一部の警告は正しくない場合があります。
ただし、誤った警告はかなり頻繁に発生するはずです。

<a id="s2.1.2-pros"></a>
<a id="212-pros"></a>

<a id="lint-pros"></a>

#### 2.1.2 Pros

タイプミス、using-vars-before-assignmentなどの見逃しやすいエラーをキャッチします。

<a id="s2.1.3-cons"></a>
<a id="213-cons"></a>

<a id="lint-cons"></a>

#### 2.1.3 Cons

`pylint` は完璧ではありません。
それを利用するために、時々それを書き留めたり、警告を抑制したり、修正したりする必要があります。

<a id="s2.1.4-decision"></a>
<a id="214-decision"></a>

<a id="lint-decision"></a>

#### 2.1.4 Decision

コードで `pylint` を実行していることを確認してください。

他の問題が隠されないように、警告が不適切な場合は警告を抑制します。
警告を抑制するために、行レベルのコメントを設定できます。

```python
dict = 'something awful'  # Bad Idea... pylint: disable=redefined-builtin
```

`pylint` の警告は、それぞれ記号名（`empty-docstring`）で識別されます。
Google固有の警告は `g-` で始まります。

記号名から抑制の理由が明確でない場合は、説明を追加してください。

この方法で抑制すると、抑制を簡単に検索して再検討できるという利点があります。

次の手順を実行すると、`pylint` 警告のリストを取得できます。

```shell
pylint --list-msgs
```

特定のメッセージの詳細を取得するには、次を使用します。

```shell
pylint --help-msg=C6409
```

`pylint：disable` を非推奨の古い形式 `pylint：disable-msg` よりも優先します。

関数の先頭にある変数を削除することで、未使用の引数の警告を抑制することができます。
削除する理由を説明するコメントを常に含めてください。
「未使用」十分なものです。例えば：

```python
def viking_cafe_order(spam, beans, eggs=None):
    del beans, eggs  # Unused by vikings.
    return spam + spam + spam
```

この警告を抑制する他の一般的な形式には、未使用の引数の識別子として '`_`' を使用するか、引数名の前に '`unused_`' を付けるか、 '`_`' に割り当てることが含まれます。
これらのフォームは許可されていますが、推奨されなくなりました。これらのブレーク呼び出し元は、名前で引数を渡し、引数が実際に使用されていないことを強制しません。

<a id="s2.2-imports"></a>
<a id="22-imports"></a>

<a id="imports"></a>

### 2.2 Imports

個々のクラスや関数ではなく、パッケージとモジュールにのみ `import` ステートメントを使用します。
[typing module](#typing-imports) からのインポートには明示的な免除があることに注意してください。

<a id="s2.2.1-definition"></a>
<a id="221-definition"></a>

<a id="imports-definition"></a>

#### 2.2.1 Definition

あるモジュールから別のモジュールにコードを共有するための再利用メカニズム。

<a id="s2.2.2-pros"></a>
<a id="222-pros"></a>

<a id="imports-pros"></a>

#### 2.2.2 Pros

名前空間の管理規則は単純です。
各識別子のソースは一貫した方法で示されます。
`x.Obj` は、オブジェクト `Obj` がモジュール `x` で定義されていることを示しています。

<a id="s2.2.3-cons"></a>
<a id="223-cons"></a>

<a id="imports-cons"></a>

#### 2.2.3 Cons

モジュール名は引き続き衝突する可能性があります。
一部のモジュール名は不便なほど長いです。

<a id="s2.2.4-decision"></a>
<a id="224-decision"></a>

<a id="imports-decision"></a>

#### 2.2.4 Decision

- パッケージとモジュールをインポートするには、`import x` を使用します。
- `from x import y` を使用します。
  ここで、`x` はパッケージプレフィックスであり、`y` はプレフィックスのないモジュール名です。
- `y` という名前の2つのモジュールをインポートする場合、または `y` が不便な長さの名前である場合は、`from x import y as z` を使用します。
- `z` が標準の略語である場合にのみ`import y as z`として使用します（たとえば、`numpy` の場合は`np`）。

たとえば、モジュール `sound.effects.echo` は次のようにインポートできます。

```python
from sound.effects import echo
...
echo.EchoFilter(input, output, delay=0.7, atten=4)
```

インポートで相対名を使用しないでください。
モジュールが同じパッケージに含まれている場合でも、完全なパッケージ名を使用してください。
これにより、意図せずにパッケージを2回インポートするのを防ぐことができます。

[typing module](#typing-imports) と
 [six.moves module](https://six.readthedocs.io/#module-six.moves) からのインポートはこのルールから免除されます。

<a id="s2.3-packages"></a>
<a id="23-packages"></a>

<a id="packages"></a>

### 2.3 Packages

モジュールの絶対パス名の場所を使用して、各モジュールをインポートします。

<a id="s2.3.1-pros"></a>
<a id="231-pros"></a>

<a id="packages-pros"></a>

#### 2.3.1 Pros

モジュールの検索パスが作成者の期待どおりでないために発生する、モジュール名の競合や誤ったインポートを回避します。
モジュールを見つけやすくします。

<a id="s2.3.2-cons"></a>
<a id="232-cons"></a>

<a id="packages-cons"></a>

#### 2.3.2 Cons

パッケージ階層を複製する必要があるため、コードのデプロイが難しくなります。
最新のデプロイメントメカニズムでは実際には問題ではありません。

<a id="s2.3.3-decision"></a>
<a id="233-decision"></a>

<a id="packages-decision"></a>

#### 2.3.3 Decision

すべての新しいコードは、完全なパッケージ名で各モジュールをインポートする必要があります。

インポートは次のようになります。

Yes:

```python
# Reference absl.flags in code with the complete name (verbose).
import absl.flags
from doctor.who import jodie

FLAGS = absl.flags.FLAGS
```

```python
# Reference flags in code with just the module name (common).
from absl import flags
from doctor.who import jodie

FLAGS = flags.FLAGS
```

No: _(このファイルが `jodie.py` も存在する `doctor/who/` にあると仮定します)_

```python
# Unclear what module the author wanted and what will be imported.  The actual
# import behavior depends on external factors controlling sys.path.
# Which possible jodie module did the author intend to import?
import jodie
```

一部の環境で発生しているにもかかわらず、メインバイナリが配置されているディレクトリが`sys.path`にあると想定しないでください。
この場合コードは、`import jodie`が、ローカルの`jodie.py`ではなく、`jodie`という名前のサードパーティまたはトップレベルのパッケージを参照していると想定する必要があります。

<a id="s2.4-exceptions"></a>
<a id="24-exceptions"></a>

<a id="exceptions"></a>

### 2.4 Exceptions

例外は許可されますが、慎重に使用する必要があります。

<a id="s2.4.1-definition"></a>
<a id="241-definition"></a>

<a id="exceptions-definition"></a>

#### 2.4.1 Definition

例外は、エラーやその他の例外的な状態を処理するために、通常の制御フローから抜け出す手段です。

<a id="s2.4.2-pros"></a>
<a id="242-pros"></a>

<a id="exceptions-pros"></a>

#### 2.4.2 Pros

通常のオペコードの制御フローは、エラー処理コードによって乱雑になりません。
また、特定の条件が発生したときに、制御フローが複数のフレームをスキップできるようにします。
たとえば、エラーコードを処理する代わりに、1つのステップでN個のネストされた関数から戻ることができます。

<a id="s2.4.3-cons"></a>
<a id="243-cons"></a>

<a id="exceptions-cons"></a>

#### 2.4.3 Cons

制御フローが混乱する可能性があります。
ライブラリ呼び出しを行うときにエラーケースを見逃しがちです。

<a id="s2.4.4-decision"></a>
<a id="244-decision"></a>

<a id="exceptions-decision"></a>

#### 2.4.4 Decision

例外は特定の条件に従う必要があります。

- 必要に応じて、組み込みの例外クラスを利用してください。
  たとえば、`ValueError`を発生させて、違反した前提条件などのプログラミングミスを示します（負の数が渡されたが正の数が必要な場合など）。
  パブリックAPIの引数値を検証するために`assert`ステートメントを使用しないでください。
  `assert` は、内部の正確性を確保するために使用され、正しい使用法を強制したり、予期しないイベントが発生したことを示したりするためには使用されません。
  後者の場合に例外が必要な場合は、raiseステートメントを使用してください。
  例えば：

  ```python
  Yes:
    def connect_to_next_port(self, minimum):
        """Connects to the next available port.

        Args:
          minimum: A port value greater or equal to 1024.

        Returns:
          The new minimum port.

        Raises:
          ConnectionError: If no available port is found.
        """
        if minimum < 1024:
          # Note that this raising of ValueError is not mentioned in the doc
          # string's "Raises:" section because it is not appropriate to
          # guarantee this specific behavioral reaction to API misuse.
          raise ValueError(f'Min. port must be at least 1024, not {minimum}.')
        port = self._find_next_open_port(minimum)
        if not port:
          raise ConnectionError(
              f'Could not connect to service on port {minimum} or higher.')
        assert port >= minimum, (
            f'Unexpected port {port} when minimum was {minimum}.')
        return port
  ```

  ```python
    No:
      def connect_to_next_port(self, minimum):
        """Connects to the next available port.

        Args:
          minimum: A port value greater or equal to 1024.

        Returns:
          The new minimum port.
        """
        assert minimum >= 1024, 'Minimum port must be at least 1024.'
        port = self._find_next_open_port(minimum)
        assert port is not None
        return port
  ```

- ライブラリまたはパッケージは、独自の例外を定義する場合があります。
  その際、既存の例外クラスから継承する必要があります。
  例外名は `Error` で終わる必要があり、スタッター（`foo.FooError`）を導入するべきではありません。
- catch-all `except:`や全ての例外をキャッチする`Exception`や`StandardError`を使用しないでください。

  - 例外を再発生させる、または
  - 例外が伝播されないが、代わりに記録および抑制される分離ポイントをプログラムに作成します。
        たとえば、スレッドの最も外側のブロックを保護することにより、スレッドがクラッシュするのを防ぎます。

    Pythonは、この点で非常に寛容です。
    ただし、名前のつづりの間違い、sys.exit）calls、Ctrl+C割り込み、単体テストの失敗、および単にキャッチしたくないその他のあらゆる種類の例外を含むすべてを実際にキャッチします。

- `try`/`except` ブロック内のコードの量を最小限に抑えます。
  `try` の本体が大きいほど、例外を発生させるとは予想していなかったコード行によって例外が発生する可能性が高くなります。
  そのような場合、`try`/`except` ブロックは実際のエラーを隠します。

- `try` ブロックで例外が発生したかどうかに関係なく、`finally` 句を使用してコードを実行します。
  これは、クリーンアップ、つまりファイルを閉じるときに役立つことがよくあります。

<a id="s2.5-global-variables"></a>
<a id="25-global-variables"></a>

<a id="global-variables"></a>

### 2.5 Global variables

グローバル変数は避けてください。

<a id="s2.5.1-definition"></a>
<a id="251-definition"></a>

<a id="global-variables-definition"></a>

#### 2.5.1 Definition

モジュールレベルまたはクラス属性として宣言されている変数。

<a id="s2.5.2-pros"></a>
<a id="252-pros"></a>

<a id="global-variables-pros"></a>

#### 2.5.2 Pros

たまに便利です。

<a id="s2.5.3-cons"></a>
<a id="253-cons"></a>

<a id="global-variables-cons"></a>

#### 2.5.3 Cons

モジュールが最初にインポートされたときにグローバル変数への割り当てが行われるため、インポート中にモジュールの動作が変更される可能性があります。

<a id="s2.5.4-decision"></a>
<a id="254-decision"></a>

<a id="global-variables-decision"></a>

#### 2.5.4 Decision

グローバル変数は避けてください。

これらは技術的には変数ですが、モジュールレベルの定数が許可および推奨されています。
次に例を示します。
`MAX_HOLY_HANDGRENADE_COUNT=3`。
定数には、アンダースコア付きのすべての大文字を使用して名前を付ける必要があります。
以下の[Naming](#s3.16-naming)を参照してください。

必要に応じて、グローバルをモジュールレベルで宣言し、名前の前に'`_`'を付けてモジュールの内部に作成する必要があります。
外部アクセスは、パブリックモジュールレベルの関数を介して実行する必要があります。
以下の[Naming](#s3.16-naming)を参照してください。

<a id="s2.6-nested"></a>
<a id="26-nested"></a>

<a id="nested-classes-functions"></a>

### 2.6 Nested/Local/Inner Classes and Functions

ネストされたローカル関数またはクラスは、ローカル変数を閉じるために使用する場合は問題ありません。
インナークラスは大丈夫です。

<a id="s2.6.1-definition"></a>
<a id="261-definition"></a>

<a id="nested-classes-functions-definition"></a>

#### 2.6.1 Definition

クラスは、メソッド、関数、またはクラスの内部で定義できます。
関数は、メソッドまたは関数内で定義できます。
ネストされた関数は、囲んでいるスコープで定義された変数に読み取り専用でアクセスできます。

<a id="s2.6.2-pros"></a>
<a id="262-pros"></a>

<a id="nested-classes-functions-pros"></a>

#### 2.6.2 Pros

非常に限られたスコープ内でのみ使用されるユーティリティクラスと関数の定義を許可します。
非常に[ADT](http://www.google.com/url?sa=D&q=http://en.wikipedia.org/wiki/Abstract_data_type)-y。
デコレータの実装に一般的に使用されます。

<a id="s2.6.3-cons"></a>
<a id="263-cons"></a>

<a id="nested-classes-functions-cons"></a>

#### 2.6.3 Cons

入れ子関数とクラスを直接テストすることはできません。
ネストすると、外部関数が長くなり、読みにくくなる可能性があります。

<a id="s2.6.4-decision"></a>
<a id="264-decision"></a>

<a id="nested-classes-functions-decision"></a>

#### 2.6.4 Decision

いくつかの注意点がありますが、問題ありません。
ローカル値を閉じる場合を除いて、ネストされた関数またはクラスは避けてください。
モジュールのユーザーから関数を隠すためだけに関数をネストしないでください。
代わりに、モジュールレベルで名前の前に_を付けて、テストで引き続きアクセスできるようにします。

<a id="s2.7-comprehensions"></a>
<a id="s2.7-list_comprehensions"></a>
<a id="27-list_comprehensions"></a>
<a id="list_comprehensions"></a>
<a id="list-comprehensions"></a>

<a id="comprehensions"></a>

### 2.7 Comprehensions & Generator Expressions

単純なケースに使用しても大丈夫です。

<a id="s2.7.1-definition"></a>
<a id="271-definition"></a>

<a id="comprehensions-definition"></a>

#### 2.7.1 Definition

List、Dict、Setの内包表記、およびジェネレーター式は、従来のループ、`map()`、`filter()`、または`lambda`を使用せずに、コンテナータイプとイテレーターを作成するための簡潔で効率的な方法を提供します。

<a id="s2.7.2-pros"></a>
<a id="272-pros"></a>

<a id="comprehensions-pros"></a>

#### 2.7.2 Pros

単純な内包表記は、他のdict、list、またはsetの作成手法よりも明確で単純な場合があります。
ジェネレータ式は、リストの作成を完全に回避するため、非常に効率的です。

<a id="s2.7.3-cons"></a>
<a id="273-cons"></a>

<a id="comprehensions-cons"></a>

#### 2.7.3 Cons

複雑な内包表記やジェネレータ式は読みにくい場合があります。

<a id="s2.7.4-decision"></a>
<a id="274-decision"></a>

<a id="comprehensions-decision"></a>

#### 2.7.4 Decision

単純なケースに使用しても大丈夫です。
各部分は1行に収まる必要があります：マッピング式、`for`句、フィルター式。
複数の`for`句またはフィルター式は許可されていません。
物事がより複雑になる場合は、代わりにループを使用してください。

```python
Yes:
  result = [mapping_expr for value in iterable if filter_expr]

  result = [{'key': value} for value in iterable
            if a_long_filter_expression(value)]

  result = [complicated_transform(x)
            for x in iterable if predicate(x)]

  descriptive_name = [
      transform({'key': key, 'value': value}, color='black')
      for key, value in generate_iterable(some_input)
      if complicated_condition_is_met(key, value)
  ]

  result = []
  for x in range(10):
      for y in range(5):
          if x * y > 10:
              result.append((x, y))

  return {x: complicated_transform(x)
          for x in long_generator_function(parameter)
          if x is not None}

  squares_generator = (x**2 for x in range(10))

  unique_names = {user.name for user in users if user is not None}

  eat(jelly_bean for jelly_bean in jelly_beans
      if jelly_bean.color == 'black')
```

```python
No:
  result = [complicated_transform(
                x, some_argument=x+1)
            for x in iterable if predicate(x)]

  result = [(x, y) for x in range(10) for y in range(5) if x * y > 10]

  return ((x, y, z)
          for x in range(5)
          for y in range(5)
          if x != y
          for z in range(5)
          if y != z)
```

<a id="s2.8-default-iterators-and-operators"></a>

<a id="default-iterators-operators"></a>

### 2.8 Default Iterators and Operators

リスト、辞書、ファイルなど、それらをサポートするタイプにはデフォルトのイテレーターと演算子を使用します。

<a id="s2.8.1-definition"></a>
<a id="281-definition"></a>

<a id="default-iterators-operators-definition"></a>

#### 2.8.1 Definition

辞書やリストなどのコンテナタイプは、デフォルトのイテレータとメンバーシップテスト演算子（"in" と "notin"）を定義します。

<a id="s2.8.2-pros"></a>
<a id="282-pros"></a>

<a id="default-iterators-operators-pros"></a>

#### 2.8.2 Pros

デフォルトのイテレータと演算子はシンプルで効率的です。
これらは、余分なメソッド呼び出しなしで、操作を直接表現します。
デフォルトの演算子を使用する関数は汎用です。
操作をサポートするすべてのタイプで使用できます。

<a id="s2.8.3-cons"></a>
<a id="283-cons"></a>

<a id="default-iterators-operators-cons"></a>

#### 2.8.3 Cons

メソッド名を読み取ってもオブジェクトのタイプを判別することはできません（たとえば、`has_key()` は辞書を意味します）。
これも利点です。

<a id="s2.8.4-decision"></a>
<a id="284-decision"></a>

<a id="default-iterators-operators-decision"></a>

#### 2.8.4 Decision

リスト、辞書、ファイルなど、それらをサポートするタイプにはデフォルトのイテレーターと演算子を使用します。
組み込み型はイテレータメソッドも定義します。
リストを返すメソッドよりもこれらのメソッドを優先します。
ただし、コンテナーを反復処理するときにコンテナーを変更しないでください。

```python
Yes:  for key in adict: ...
      if key not in adict: ...
      if obj in alist: ...
      for line in afile: ...
      for k, v in adict.items(): ...
      for k, v in six.iteritems(adict): ...
```

```python
No:   for key in adict.keys(): ...
      if not adict.has_key(key): ...
      for line in afile.readlines(): ...
      for k, v in dict.iteritems(): ...
```

<a id="s2.9-generators"></a>
<a id="29-generators"></a>

<a id="generators"></a>

### 2.9 Generators

必要に応じてジェネレーターを使用してください。

<a id="s2.9.1-definition"></a>
<a id="291-definition"></a>

<a id="generators-definition"></a>

#### 2.9 Definition

ジェネレーター関数は、yieldステートメントを実行するたびに値を生成するイテレーターを返します。
値が生成された後、次の値が必要になるまで、ジェネレーター関数の実行時の状態が一時停止されます。

<a id="s2.9.2-pros"></a>
<a id="292-pros"></a>

<a id="generators-pros"></a>

#### 2.9.2 Pros

ローカル変数の状態と制御フローが呼び出しごとに保持されるため、コードが単純になります。
ジェネレーターは、値のリスト全体を一度に作成する関数よりも少ないメモリーを使用します。

<a id="s2.9.3-cons"></a>
<a id="293-cons"></a>

<a id="generators-cons"></a>

#### 2.9.3 Cons

None.

<a id="s2.9.4-decision"></a>
<a id="294-decision"></a>

<a id="generators-decision"></a>

#### 2.9.4 Decision

結構です。
ジェネレーター関数のdocstringでは、"Returns:"ではなく"Yields:"を使用してください。

<a id="s2.10-lambda-functions"></a>
<a id="210-lambda-functions"></a>

<a id="lambdas"></a>

### 2.10 Lambda Functions

ワンライナーで大丈夫。
`lambda` を使用した `map()` または `filter()` よりもジェネレーター式を優先します。

<a id="s2.10.1-definition"></a>
<a id="2101-definition"></a>

<a id="lambdas-definition"></a>

#### 2.10.1 Definition

ラムダは、ステートメントではなく、式で無名関数を定義します。

<a id="s2.10.2-pros"></a>
<a id="2102-pros"></a>

<a id="lambdas-pros"></a>

#### 2.10.2 Pros

便利。

<a id="s2.10.3-cons"></a>
<a id="2103-cons"></a>

<a id="lambdas-cons"></a>

#### 2.10.3 Cons

ローカル関数よりも読み取りとデバッグが困難です。
名前がないということは、スタックトレースを理解するのがより難しいことを意味します。
関数には式のみが含まれる可能性があるため、表現力は制限されます。

<a id="s2.10.4-decision"></a>
<a id="2104-decision"></a>

<a id="lambdas-decision"></a>

#### 2.10.4 Decision

ワンライナーに使用しても大丈夫です。
ラムダ関数内のコードが60〜80文字より長い場合は、通常の [nested function](#lexical-scoping)として定義することをお勧めします。
乗算などの一般的な演算では、ラムダ関数の代わりに`operator`の関数を使用します。
たとえば、`lambda x, y: x * y`より`operator.mul`を優先します。

<a id="s2.11-conditional-expressions"></a>
<a id="211-conditional-expressions"></a>

<a id="conditional-expressions"></a>

### 2.11 Conditional Expressions

単純なケースでも大丈夫です。

<a id="s2.11.1-definition"></a>
<a id="2111-definition"></a>

<a id="conditional-expressions-definition"></a>

#### 2.11.1 Definition

条件式（"三項演算子"と呼ばれることもあります）は、ifステートメントの構文を短くするメカニズムです。
例：`x = 1 if cond else 2`

<a id="s2.11.2-pros"></a>
<a id="2112-pros"></a>

<a id="conditional-expressions-pros"></a>

#### 2.11.2 Pros

ifステートメントよりも短くて便利です。

<a id="s2.11.3-cons"></a>
<a id="2113-cons"></a>

<a id="conditional-expressions-cons"></a>

#### 2.11.3 Cons

ifステートメントよりも読みにくい場合があります。
式が長いと、条件を特定するのが難しい場合があります。

<a id="s2.11.4-decision"></a>
<a id="2114-decision"></a>

<a id="conditional-expressions-decision"></a>

#### 2.11.4 Decision

単純なケースに使用しても大丈夫です。
各部分は、true-expression、if-expression、else-expressionの1行に収まる必要があります。
事態がさらに複雑になる場合は、完全なifステートメントを使用してください。

```python
Yes:
    one_line = 'yes' if predicate(value) else 'no'
    slightly_split = ('yes' if predicate(value)
                      else 'no, nein, nyet')
    the_longest_ternary_style_that_can_be_done = (
        'yes, true, affirmative, confirmed, correct'
        if predicate(value)
        else 'no, false, negative, nay')
```

```python
No:
    bad_line_breaking = ('yes' if predicate(value) else
                         'no')
    portion_too_long = ('yes'
                        if some_long_module.some_long_predicate_function(
                            really_long_variable_name)
                        else 'no, false, negative, nay')
```

<a id="s2.12-default-argument-values"></a>
<a id="212-default-argument-values"></a>

<a id="default-arguments"></a>

### 2.12 Default Argument Values

ほとんどの場合大丈夫です。

<a id="s2.12.1-definition"></a>
<a id="2121-definition"></a>

<a id="default-arguments-definition"></a>

#### 2.12.1 Definition

関数のパラメータリストの最後に変数の値を指定できます（例：`def foo(a, b=0):` `foo`が1つの引数のみで呼び出された場合、`b`は0に設定されます。
2つの引数で呼び出された場合、`b`は2番目の引数の値を持ちます。

<a id="s2.12.2-pros"></a>
<a id="2122-pros"></a>

<a id="default-arguments-pros"></a>

#### 2.12.2 Pros

多くの場合、多くのデフォルト値を使用する関数がありますが、まれにデフォルトをオーバーライドしたい場合があります。
デフォルトの引数値は、まれな例外のために多くの関数を定義する必要なしに、これを行う簡単な方法を提供します。
Pythonはオーバーロードされたメソッド/関数をサポートしていないため、デフォルトの引数はオーバーロード動作を「偽造」する簡単な方法です。

<a id="s2.12.3-cons"></a>
<a id="2123-cons"></a>

<a id="default-arguments-cons"></a>

#### 2.12.3 Cons

デフォルトの引数は、モジュールのロード時に1回評価されます。
引数がリストや辞書などの可変オブジェクトである場合、これにより問題が発生する可能性があります。
関数がオブジェクトを変更する場合（たとえば、リストに項目を追加することによって）、デフォルト値が変更されます。

<a id="s2.12.4-decision"></a>
<a id="2124-decision"></a>

<a id="default-arguments-decision"></a>

#### 2.12.4 Decision

次の注意事項を使用して使用できます。
関数またはメソッド定義のデフォルト値として可変オブジェクトを使用しないでください。

```python
Yes: def foo(a, b=None):
         if b is None:
             b = []
Yes: def foo(a, b: Optional[Sequence] = None):
         if b is None:
             b = []
Yes: def foo(a, b: Sequence = ()):  # Empty tuple OK since tuples are immutable
         ...
```

```python
No:  def foo(a, b=[]):
         ...
No:  def foo(a, b=time.time()):  # The time the module was loaded???
         ...
No:  def foo(a, b=FLAGS.my_thing):  # sys.argv has not yet been parsed...
         ...
No:  def foo(a, b: Mapping = {}):  # Could still get passed to unchecked code
         ...
```

<a id="s2.13-properties"></a>
<a id="213-properties"></a>

<a id="properties"></a>

### 2.13 Properties

シンプルで軽量なアクセサーまたはセッターメソッドを通常使用する場所で、データにアクセスまたは設定するためのプロパティを使用します。

<a id="s2.13.1-definition"></a>
<a id="2131-definition"></a>

<a id="properties-definition"></a>

#### 2.13.1 Definition

メソッド呼び出しをラップする方法では、計算が軽量な場合に、標準の属性アクセスとして属性を取得および設定する必要があります。

<a id="s2.13.2-pros"></a>
<a id="2132-pros"></a>

<a id="properties-pros"></a>

#### 2.13.2 Pros

単純な属性アクセスのための明示的なgetおよびsetメソッド呼び出しを排除することにより、読みやすさが向上します。計算を怠惰にすることができます。
クラスのインターフェースを維持するためのPythonの方法を検討しました。
パフォーマンスの観点から、プロパティを許可すると、直接変数アクセスが妥当な場合に、簡単なアクセサメソッドを必要とせずにバイパスされます。
これにより、インターフェイスを壊すことなく、アクセサメソッドを将来追加することもできます。

<a id="s2.13.3-cons"></a>
<a id="2133-cons"></a>

<a id="properties-cons"></a>

#### 2.13.3 Cons

演算子のオーバーロードのような副作用を隠すことができます。
サブクラスを混乱させる可能性があります。

<a id="s2.13.4-decision"></a>
<a id="2134-decision"></a>

<a id="properties-decision"></a>

#### 2.13.4 Decision

新しいコードのプロパティを使用して、通常は軽量のaccessorまたはsetterメソッドを使用していたデータにアクセスまたはセットします。
プロパティは、`@property` [decorator](#s2.17-function-and-method-decorators)を使用して作成する必要があります。

プロパティ自体がオーバーライドされていない場合、プロパティの継承は自明ではない可能性があります。
したがって、サブクラスでオーバーライドされたメソッドがプロパティによって呼び出されるように、アクセサメソッドが間接的に呼び出されることを確認する必要があります。
[template method design pattern](https://en.wikipedia.org/wiki/Template_method_pattern)を使用。

```python
Yes: import math

     class Square:
         """A square with two properties: a writable area and a read-only perimeter.

         To use:
         >>> sq = Square(3)
         >>> sq.area
         9
         >>> sq.perimeter
         12
         >>> sq.area = 16
         >>> sq.side
         4
         >>> sq.perimeter
         16
         """

         def __init__(self, side):
             self.side = side

         @property
         def area(self):
             """Area of the square."""
             return self._get_area()

         @area.setter
         def area(self, area):
             return self._set_area(area)

         def _get_area(self):
             """Indirect accessor to calculate the 'area' property."""
             return self.side ** 2

         def _set_area(self, area):
             """Indirect setter to set the 'area' property."""
             self.side = math.sqrt(area)

         @property
         def perimeter(self):
             return self.side * 4
```

<a id="s2.14-truefalse-evaluations"></a>
<a id="214-truefalse-evaluations"></a>

<a id="truefalse-evaluations"></a>

### 2.14 True/False Evaluations

可能であれば、"implicit(暗黙)" のfalseを使用してください。

<a id="s2.14.1-definition"></a>
<a id="2141-definition"></a>

<a id="truefalse-evaluations-definition"></a>

#### 2.14.1 Definition

Pythonは、ブール値のコンテキストでは、特定の値を`False`として評価します。
簡単な"rule of thumb(経験則)"では、すべての「空の」値はfalseと見なされるため、`0、None、[]、{}、''`はすべてブールコンテキストでfalseと評価されます。

<a id="s2.14.2-pros"></a>
<a id="2142-pros"></a>

<a id="truefalse-evaluations-pros"></a>

#### 2.14.2 Pros

Pythonブール値を使用する条件は読みやすく、エラーが発生しにくくなります。
ほとんどの場合、それらも高速です。

<a id="s2.14.3-cons"></a>
<a id="2143-cons"></a>

<a id="truefalse-evaluations-cons"></a>

#### 2.14.3 Cons

C/C++開発者には奇妙に見えるかもしれません。

<a id="s2.14.4-decision"></a>
<a id="2144-decision"></a>

<a id="truefalse-evaluations-decision"></a>

#### 2.14.4 Decision

可能であれば、"implicit(暗黙)" falseを使用します。
`if foo！=[]`：ではなく `if foo：`の 場合です。
ただし、覚えておくべきいくつかの注意事項があります。

- `None`値をチェックするためには `if foo is None:` を常に使用します:(または `is not None`）
    たとえば、デフォルトで `None` に設定されている変数または引数が他の値に設定されているかどうかをテストする場合。
    他の値は、ブール値のコンテキストではfalseの値である可能性があります。
- `==` を使用してブール変数を `False` と比較しないでください。
    `if not x:` を代わりに使用します。
    `False` と `None` を区別する必要がある場合は、`if not x and x is not None:` のように式をチェーンします。
- シーケンス（文字列、リスト、タプル）の場合は、空のシーケンスがfalseであるという事実を使用します。
    したがって、`if seq:` と`if not seq:` の場合は、`if len(seq):` と`if not len(seq):` よりもそれぞれ優先されます。
- 整数を処理する場合、暗黙のfalseは、利益よりもリスクが高くなる可能性があります（つまり、誤って `None` を0として処理する）。
    整数であることがわかっている（そして `len()` の結果ではない）値を整数0と比較することができます。

    ```python
    Yes: if not users:
             print('no users')

         if foo == 0:
             self.handle_zero()

         if i % 10 == 0:
             self.handle_multiple_of_ten()

         def f(x=None):
             if x is None:
                 x = []
    ```

    ```python
    No:  if len(users) == 0:
             print('no users')

         if foo is not None and not foo:
             self.handle_zero()

         if not i % 10:
             self.handle_multiple_of_ten()

         def f(x=None):
             x = x or []
    ```

- '0'（つまり、文字列としての0）はtrueと評価されることに注意してください。

<a id="s2.16-lexical-scoping"></a>
<a id="216-lexical-scoping"></a>

<a id="lexical-scoping"></a>

### 2.16 Lexical Scoping

使用しても大丈夫です。

<a id="s2.16.1-definition"></a>
<a id="2161-definition"></a>

<a id="lexical-scoping-definition"></a>

#### 2.16.1 Definition

ネストされたPython関数は、囲んでいる関数で定義された変数を参照できますが、それらに割り当てることはできません。
変数バインディングは、字句スコープを使用して、つまり静的プログラムテキストに基づいて解決されます。
ブロック内の名前への割り当てにより、Pythonは、使用が割り当ての前にある場合でも、その名前へのすべての参照をローカル変数として扱います。
グローバル宣言が発生した場合、その名前はグローバル変数として扱われます。

この機能の使用例は次のとおりです。

```python
def get_adder(summand1):
    """Returns a function that adds numbers to a given number."""
    def adder(summand2):
        return summand1 + summand2

    return adder
```

<a id="s2.16.2-pros"></a>
<a id="2162-pros"></a>

<a id="lexical-scoping-pros"></a>

#### 2.16.2 Pros

多くの場合、より明確でエレガントなコードになります。
特に経験豊富なLispとScheme（そしてHaskellとMLと...）プログラマーにとっては慰めです。

<a id="s2.16.3-cons"></a>
<a id="2163-cons"></a>

<a id="lexical-scoping-cons"></a>

#### 2.16.3 Cons

紛らわしいバグにつながる可能性があります。
[PEP-0227](http://www.google.com/url?sa=D&q=http://www.python.org/dev/peps/pep-0227/)に基づくこの例のように：

```python
i = 4
def foo(x):
    def bar():
        print(i, end='')
    # ...
    # A bunch of code here
    # ...
    for i in x:  # Ah, i *is* local to foo, so this is what bar sees
        print(i, end='')
    bar()
```

したがって、`foo[1,2,3])`は `1 2 3 4` ではなく `1 2 3 3` を出力します。

<a id="s2.16.4-decision"></a>
<a id="2164-decision"></a>

<a id="lexical-scoping-decision"></a>

#### 2.16.4 Decision

使用しても大丈夫です。

<a id="s2.17-function-and-method-decorators"></a>
<a id="217-function-and-method-decorators"></a>
<a id="function-and-method-decorators"></a>

<a id="decorators"></a>

### 2.17 Function and Method Decorators

明らかな利点がある場合は、デコレータを慎重に使用してください。
`staticmethod` を避け、`classmethod` の使用を制限します。

<a id="s2.17.1-definition"></a>
<a id="2171-definition"></a>

<a id="decorators-definition"></a>

#### 2.17.1 Definition

[Decorators for Functions and Methods](https://docs.python.org/3/glossary.html#term-decorator)（別名「@表記」）。
一般的なデコレータの1つは`@property`で、通常のメソッドを動的に計算される属性に変換するために使用されます。
ただし、デコレータ構文では、ユーザー定義のデコレータも使用できます。
具体的には、一部の関数`my_decorator`の場合、次のようになります。

```python
class C:
    @my_decorator
    def method(self):
        # method body ...
```

is equivalent to:

```python
class C:
    def method(self):
        # method body ...
    method = my_decorator(method)
```

<a id="s2.17.2-pros"></a>
<a id="2172-pros"></a>

<a id="decorators-pros"></a>

#### 2.17.2 Pros

メソッドの変換をエレガントに指定します。
変換により、反復的なコードが削除されたり、不変条件が適用されたりする場合があります。

<a id="s2.17.3-cons"></a>
<a id="2173-cons"></a>

<a id="decorators-cons"></a>

#### 2.17.3 Cons

デコレータは、関数の引数または戻り値に対して任意の操作を実行できるため、驚くべき暗黙の動作が発生します。
さらに、デコレータはインポート時に実行されます。
デコレータコードの障害から回復することはほとんど不可能です。

<a id="s2.17.4-decision"></a>
<a id="2174-decision"></a>

<a id="decorators-decision"></a>

#### 2.17.4 Decision

明らかな利点がある場合は、デコレータを慎重に使用してください。
デコレータは、関数と同じインポートおよび命名ガイドラインに従う必要があります。
デコレータpydocは、関数がデコレータであることを明確に示す必要があります。
デコレータの単体テストを作成します。

デコレータ自体の外部依存関係を回避します（たとえば、ファイル、ソケット、データベース接続などに依存しないでください）。
デコレータの実行時に（インポート時に、おそらく`pydoc`または他のツールから利用できない可能性があるためです。
有効なパラメータで呼び出されるデコレータは、（可能な限り）すべての場合に成功することが保証されている必要があります。

デコレータは「トップレベルコード」の特殊なケースです。
詳細については、[main](#s3.17-main) を参照してください。

既存のライブラリで定義されているAPIと統合するために強制されない限り、`staticmethod` を使用しないでください。
代わりに、モジュールレベルの関数を記述してください。

`classmethod` は、名前付きコンストラクター、またはプロセス全体のキャッシュなどの必要なグローバル状態を変更するクラス固有のルーチンを作成する場合にのみ使用してください。

<a id="s2.18-threading"></a>
<a id="218-threading"></a>

<a id="threading"></a>

### 2.18 Threading

組み込み型のアトミック性に依存しないでください。

dictionariesなどのPythonの組み込みデータ型にはアトミック操作があるように見えますが、アトミックではない場合があり（たとえば、`__hash__`または`__eq__`がPythonメソッドとして実装されている場合）、それらのアトミック性に依存するべきではありません。
また、アトミック変数の割り当てに依存するべきではありません（これはdictionariesに依存するため）。

スレッド間でデータを通信するための推奨される方法として、キューモジュールの`Queue`データ型を使用します。
それ以外の場合は、スレッドモジュールとそのロックプリミティブを使用します。
下位レベルのロックを使用する代わりに、条件変数と`threading.Condition`を優先します。

<a id="s2.19-power-features"></a>
<a id="219-power-features"></a>

<a id="power-features"></a>

### 2.19 Power Features

これらの機能は避けてください。

<a id="s2.19.1-definition"></a>
<a id="2191-definition"></a>

<a id="power-features-definition"></a>

#### 2.19.1 Definition

Pythonは非常に柔軟な言語であり、カスタムメタクラス、バイトコードへのアクセス、オンザフライコンパイル、動的継承、オブジェクトの親の変更、インポートハック、リフレクション`getattr()`の一部の使用など）、システム内部など

<a id="s2.19.2-pros"></a>
<a id="2192-pros"></a>

<a id="power-features-pros"></a>

#### 2.19.2 Pros

これらは強力な言語機能です。コードをよりコンパクトにすることができます。

<a id="s2.19.3-cons"></a>
<a id="2193-cons"></a>

<a id="power-features-cons"></a>

#### 2.19.3 Cons

絶対に必要ではないときに、これらの「クールな」機能を使用するのは非常に魅力的です。
下にある異常な機能を使用しているコードを読んだり、理解したり、デバッグしたりするのは困難です。
最初は（元の作成者には）そのようには見えませんが、コードを再検討すると、長いが単純なコードよりも難しい傾向があります。

<a id="s2.19.4-decision"></a>
<a id="2194-decision"></a>

<a id="power-features-decision"></a>

#### 2.19.4 Decision

コードでこれらの機能を避けてください。

これらの機能を内部的に使用する標準ライブラリモジュールおよびクラス（たとえば、`abc.ABCMeta`、`dataclasses`、および`enum`は使用できます。

<a id="s2.20-modern-python"></a>
<a id="220-modern-python"></a>

<a id="modern-python"></a>

### 2.20 Modern Python: Python 3 and from \_\_future\_\_ imports

Python3が登場！
すべてのプロジェクトがまだそれを使用する準備ができているわけではありませんが、すべてのコードは3互換になるように作成する必要があります。
（可能な場合は3でテストします）。

<a id="s2.20.1-definition"></a>
<a id="2201-definition"></a>

<a id="modern-python-definition"></a>

#### 2.20.1 Definition

Python3は、Python言語の重要な変更です。
既存のコードは2.7を念頭に置いて記述されることがよくありますが、コードの意図をより明確にし、Python3で変更せずに使用できるように準備するための簡単な方法がいくつかあります。

<a id="s2.20.2-pros"></a>
<a id="2202-pros"></a>

<a id="modern-python-pros"></a>

#### 2.20.2 Pros

Python3を念頭に置いて記述されたコードは、プロジェクトのすべての依存関係の準備ができたら、Python 3でより明確になり、実行しやすくなります。

<a id="s2.20.3-cons"></a>
<a id="2203-cons"></a>

<a id="modern-python-cons"></a>

#### 2.20.3 Cons

一部の人々は、追加の定型文が醜いと感じています。
インポートによって追加された機能を実際に必要としないモジュールにインポートを追加することは珍しいことです。

<a id="s2.20.4-decision"></a>
<a id="2204-decision"></a>

<a id="modern-python-decision"></a>

#### 2.20.4 Decision

##### from \_\_future\_\_ imports

`from __future__import` ステートメントの使用をお勧めします。
すべての新しいコードには次のものが含まれている必要があり、可能な場合は既存のコードを更新して互換性を持たせる必要があります。

```python
from __future__ import absolute_import
from __future__ import division
from __future__ import print_function
```

これらのインポートの詳細については、
[absolute imports](https://www.python.org/dev/peps/pep-0328/)、
[`/` division behavior](https://www.python.org/dev/peps/pep-0238/)、
および[the `print` function](https://www.python.org/dev/peps/pep-3105/)
を参照してください。

コードがPython3のみである場合を除き、現在モジュールで使用されていない場合でも、これらのインポートを省略または削除しないでください。 誰かがそのような機能を使い始めた後の編集中にそれらが忘れられないように、すべてのファイルに将来のインポートを常に持つことをお勧めします。

`__future__import` ステートメントから他のものがあります。
必要に応じて使用してください。`unicode_literals` は、Python2.7内の多くの場所で暗黙的なデフォルトのコーデック変換の結果をもたらすため、明確な勝利ではないため、推奨事項には含めません。
ほとんどのコードは、必要に応じて `b''` および `u''` バイトとUnicode文字列リテラルを明示的に使用する方が適切です。

##### The six, future, and past libraries

プロジェクトでPython2と3の両方での使用を積極的にサポートする必要がある場合は、適切と思われる[six](https://pypi.org/project/six/)、[future](https://pypi.org/project/future/)、および[past](https://pypi.org/project/past/)のライブラリを使用してください。
これらは、コードをよりクリーンにし、作業を楽にするために存在します。

<a id="s2.21-type-annotated-code"></a>
<a id="s2.21-typed-code"></a>
<a id="221-type-annotated-code"></a>
<a id="typed-code"></a>

<a id="typed-code"></a>

### 2.21 Type Annotated Code

[PEP-484](https://www.python.org/dev/peps/pep-0484/)に従ってタイプヒントでPython3コードに注釈を付け、[pytype](https://github.com/google/pytype)などのタイプチェックツールを使用してビルド時にコードをタイプチェックできます。

型注釈は、ソースまたは[stub pyi file](https://www.python.org/dev/peps/pep-0484/#stub-files)に含めることができます。
可能な限り、注釈はソースに含める必要があります。サードパーティまたは拡張モジュールにはpyiファイルを使用します。

<a id="s2.21.1-definition"></a>
<a id="2211-definition"></a>

<a id="typed-code-definition"></a>

#### 2.21.1 Definition

型注釈（または「型ヒント」）は、関数またはメソッドの引数と戻り値用です。

```python
def func(a: int) -> List[int]:
```

同様の [PEP-526](https://www.python.org/dev/peps/pep-0526/) 構文を使用して、変数の型を宣言することもできます。

```python
a: SomeType = some_func()
```

または、レガシーPythonバージョンをサポートする必要があるコードでタイプコメントを使用する。

```python
a = some_func()  # type: SomeType
```

<a id="s2.21.2-pros"></a>
<a id="2212-pros"></a>

<a id="typed-code-pros"></a>

#### 2.21.2 Pros

型注釈により、コードの可読性と保守性が向上します。
タイプチェッカーは、多くのランタイムエラーをビルド時エラーに変換し、[Power Features](#power-features)を使用する能力を低下させます。

<a id="s2.21.3-cons"></a>
<a id="2213-cons"></a>

<a id="typed-code-cons"></a>

#### 2.21.3 Cons

型宣言を最新の状態に保つ必要があります。
有効なコードであると思われるタイプエラーが表示される場合があります。
[type checker](https://github.com/google/pytype)を使用すると、[Power Features](#power-features)を使用する能力が低下する場合があります。

<a id="s2.21.4-decision"></a>
<a id="2214-decision"></a>

<a id="typed-code-decision"></a>

#### 2.21.4 Decision

コードを更新するときは、Python型分析を有効にすることを強くお勧めします。
パブリックAPIを追加または変更するときは、タイプアノテーションを含め、ビルドシステムでpytypeを介したチェックを有効にします。
静的分析はPythonにとって比較的新しいため、望ましくない副作用（誤って推測された型など）が一部のプロジェクトでの採用を妨げる可能性があることを認識しています。
そのような状況では、作成者はTODOを含むコメントを追加するか、BUILDファイルまたはコード自体で現在タイプアノテーションの採用を妨げている問題を説明するバグへのリンクを適宜追加することをお勧めします。

<a id="s3-python-style-rules"></a>
<a id="3-python-style-rules"></a>

<a id="python-style-rules"></a>

## 3 Python Style Rules

<a id="s3.1-semicolons"></a>
<a id="31-semicolons"></a>

<a id="semicolons"></a>

### 3.1 Semicolons

行をセミコロンで終了したり、セミコロンを使用して2つのステートメントを同じ行に配置したりしないでください。

<a id="s3.2-line-length"></a>
<a id="32-line-length"></a>

<a id="line-length"></a>

### 3.2 Line length

最大行長は*80文字*です。

80文字の制限に対する明示的な例外：

- 長い import ステートメント。
- URL、パス名、またはコメント内の長いフラグ。
- URLやパス名などの行に分割するのに不便な空白を含まない長い文字列モジュールレベル定数。
  - Pylintはコメントを無効にします。(たとえば: `# pylint: disable=invalid-name`)

3つ以上のコンテキスト・マネージャーを必要とするステートメントを除いて、バックスラッシュを使用しないでください。

[implicit line joining inside parentheses, brackets and braces](http://docs.python.org/reference/lexical_analysis.html#implicit-line-joining)を利用します。
必要に応じて、式の前後に括弧のペアを追加できます。

```python
Yes: foo_bar(self, width, height, color='black', design=None, x='foo',
             emphasis=None, highlight=0)

     if (width == 0 and height == 0 and
         color == 'red' and emphasis == 'strong'):
```

リテラル文字列が1行に収まらない場合は、暗黙の行結合に括弧を使用します。

```python
x = ('This will build a very long long '
     'long long long long long long string')
```

コメント内で、必要に応じて長いURLを独自の行に配置します。

```python
Yes:  # See details at
      # http://www.example.com/us/developer/documentation/api/content/v2.0/csv_file_name_extension_full_specification.html
```

```python
No:  # See details at
     # http://www.example.com/us/developer/documentation/api/content/\
     # v2.0/csv_file_name_extension_full_specification.html
```

式が3行以上にまたがる `with` ステートメントを定義する場合は、バックスラッシュを使用できます。 2行の式の場合、ネストされた `with` ステートメントを使用します。

```python
Yes:  with very_long_first_expression_function() as spam, \
           very_long_second_expression_function() as beans, \
           third_thing() as eggs:
          place_order(eggs, beans, spam, beans)
```

```python
No:  with VeryLongFirstExpressionFunction() as spam, \
          VeryLongSecondExpressionFunction() as beans:
       PlaceOrder(eggs, beans, spam, beans)
```

```python
Yes:  with very_long_first_expression_function() as spam:
          with very_long_second_expression_function() as beans:
              place_order(beans, spam)
```

上記の行継続の例の要素のインデントに注意してください。 説明については、[indentation](#s3.4-indentation) のセクションを参照してください。

行が80文字を超え、[yapf](https://github.com/google/yapf/) 自動フォーマッタが行を制限未満にするのに役立たない他のすべての場合、行はこの最大値を超えることができます。

<a id="s3.3-parentheses"></a>
<a id="33-parentheses"></a>

<a id="parentheses"></a>

### 3.3 Parentheses (カッコ)

括弧は慎重に使用してください。

必須ではありませんが、タプルを括弧で囲むことは問題ありません。
暗黙の行継続またはタプルを示すために括弧を使用しない限り、returnステートメントまたは条件ステートメントでそれらを使用しないでください。

```python
Yes: if foo:
         bar()
     while x:
         x = bar()
     if x and y:
         bar()
     if not x:
         bar()
     # For a 1 item tuple the ()s are more visually obvious than the comma.
     onesie = (foo,)
     return foo
     return spam, beans
     return (spam, beans)
     for (x, y) in dict.items(): ...
```

```python
No:  if (x):
         bar()
     if not(x):
         bar()
     return (foo)
```

<a id="s3.4-indentation"></a>
<a id="34-indentation"></a>

<a id="indentation"></a>

### 3.4 Indentation (インデント)

コードブロックを *4つのスペース* でインデントします。

タブを使用したり、タブとスペースを混在させたりしないでください。
暗黙の行継続の場合は、[line length](#s3.2-line-length) セクションの例のように、ラップされた要素を垂直方向に揃える必要があります。
または、4つのスペースのぶら下げインデントを使用します。
この場合、最初の行の開き括弧または角かっこの後には何もありません。

```python
Yes:   # Aligned with opening delimiter
       foo = long_function_name(var_one, var_two,
                                var_three, var_four)
       meal = (spam,
               beans)

       # Aligned with opening delimiter in a dictionary
       foo = {
           long_dictionary_key: value1 +
                                value2,
           ...
       }

       # 4-space hanging indent; nothing on first line
       foo = long_function_name(
           var_one, var_two, var_three,
           var_four)
       meal = (
           spam,
           beans)

       # 4-space hanging indent in a dictionary
       foo = {
           long_dictionary_key:
               long_dictionary_value,
           ...
       }
```

```python
No:    # Stuff on first line forbidden
       foo = long_function_name(var_one, var_two,
           var_three, var_four)
       meal = (spam,
           beans)

       # 2-space hanging indent forbidden
       foo = long_function_name(
         var_one, var_two, var_three,
         var_four)

       # No hanging indent in a dictionary
       foo = {
           long_dictionary_key:
           long_dictionary_value,
           ...
       }
```

<a id="s3.4.1-trailing-comma"></a>
<a id="s3.4.1-trailing-commas"></a>
<a id="s3.4.1-trailing_comma"></a>
<a id="s3.4.1-trailing_commas"></a>
<a id="341-trailing_comma"></a>
<a id="341-trailing_commas"></a>
<a id="trailing_comma"></a>
<a id="trailing_commas"></a>

<a id="trailing-comma"></a>

### 3.4.1 Trailing commas in sequences of items? (アイテムのシーケンスの末尾のコンマ？)

アイテムのシーケンスの末尾のコンマは、終了コンテナトークン `]`、`)`、または `}`  が最後の要素と同じ行に表示されない場合にのみ推奨されます。
末尾のコンマの存在は、Pythonコードオートフォーマッター[YAPF](https://pypi.org/project/yapf/)へのヒントとしても使用され、
最後の要素が存在する後の `,` の場合に、アイテムのコンテナーを1行に1つのアイテムに自動フォーマットするように指示します。

```python
Yes:   golomb3 = [0, 1, 3]
Yes:   golomb4 = [
           0,
           1,
           4,
           6,
       ]
```

```python
No:    golomb4 = [
           0,
           1,
           4,
           6
       ]
```

<a id="s3.5-blank-lines"></a>
<a id="35-blank-lines"></a>

<a id="blank-lines"></a>

### 3.5 Blank Lines (空白行)

関数定義であれクラス定義であれ、最上位の定義の間に2行の空白行があります。
メソッド定義間、および`class`と最初のメソッド間の1行の空白行。
`def` の後に空白行はありません。関数またはメソッド内で適切と判断する場合は、1行の空白行を使用してください。

<a id="s3.6-whitespace"></a>
<a id="36-whitespace"></a>

<a id="whitespace"></a>

### 3.6 Whitespace (空白)

句読点の前後のスペースの使用については、標準の活版印刷規則に従ってください。

括弧、角かっこ、中括弧の内側に空白はありません。

```python
Yes: spam(ham[1], {eggs: 2}, [])
```

```python
No:  spam( ham[ 1 ], { eggs: 2 }, [ ] )
```

コンマ、セミコロン、またはコロンの前に空白はありません。
行の終わりを除いて、コンマ、セミコロン、またはコロンの後に空白を使用してください。

```python
Yes: if x == 4:
         print(x, y)
     x, y = y, x
```

```python
No:  if x == 4 :
         print(x , y)
     x , y = y , x
```

引数リスト、インデックス付け、またはスライスを開始するオープンパレン/ブラケットの前に空白はありません。

```python
Yes: spam(1)
```

```python
No:  spam (1)
```

```python
Yes: dict['key'] = list[index]
```

```python
No:  dict ['key'] = list [index]
```

末尾に空白はありません。

(`=`)、比較の(`==, <, >, !=, <>, <=, >=, in, not in, is, is not`)、およびブール値(`and, or, not`)のために、両側に1つのスペースで二項演算子を囲みます。
算術演算子( `+`, `-`, `*`, `/`, `//`, `%`, `**`, `@` )の周りスペースの挿入については、より適切な判断を使用してください。

```python
Yes: x == 1
```

```python
No:  x<1
```

キーワード引数を渡すとき、またはデフォルトのパラメータ値を定義するときは、`=`の前後にスペースを使用しないでください。
ただし、型注釈が存在する場合([when a type annotation is present](#typing-default-values))は、
デフォルトのパラメータ値に `=` の前後にスペースを使用してください。

```python
Yes: def complex(real, imag=0.0): return Magic(r=real, i=imag)
Yes: def complex(real, imag: float = 0.0): return Magic(r=real, i=imag)
```

```python
No:  def complex(real, imag = 0.0): return Magic(r = real, i = imag)
No:  def complex(real, imag: float=0.0): return Magic(r = real, i = imag)
```

Don't use spaces to vertically align tokens on consecutive lines, since it
becomes a maintenance burden (applies to `:`, `#`, `=`, etc.):

トークンを連続する行に垂直に配置するためにスペースを使用しないでください。
メンテナンスの負担になります（ `：` 、`#` 、`=` などに適用されます）。

```python
Yes:
  foo = 1000  # comment
  long_name = 2  # comment that should not be aligned

  dictionary = {
      'foo': 1,
      'long_name': 2,
  }
```

```python
No:
  foo       = 1000  # comment
  long_name = 2     # comment that should not be aligned

  dictionary = {
      'foo'      : 1,
      'long_name': 2,
  }
```

<a id="Python_Interpreter"></a>
<a id="s3.7-shebang-line"></a>
<a id="37-shebang-line"></a>

<a id="shebang-line"></a>

### 3.7 Shebang Line

ほとんどの`.py`ファイルは`#!`で始まる必要はありません。
プログラムのメインファイルを、[PEP-394](https://www.python.org/dev/peps/pep-0394/)に従って
`#!/usr/bin/env python3`（virtualenvsをサポートするため）または`#!/usr/bin/python3` で開始します。

この行は、カーネルがPythonインタープリターを見つけるために使用しますが、モジュールをインポートするときにPythonによって無視されます。
直接実行することを目的としたファイルでのみ必要です。

<a id="s3.8-comments-and-docstrings"></a>
<a id="s3.8-comments"></a>
<a id="38-comments-and-docstrings"></a>

<a id="documentation"></a>

### 3.8 Comments and Docstrings

モジュール、関数、メソッドdocstring、およびインラインコメントには必ず正しいスタイルを使用してください。

<a id="s3.8.1-comments-in-doc-strings"></a>
<a id="381-docstrings"></a>
<a id="comments-in-doc-strings"></a>

<a id="docstrings"></a>

#### 3.8.1 Docstrings

Pythonはdocstringを使用してコードを文書化します。
docstringは、パッケージ、モジュール、クラス、または関数の最初のステートメントである文字列です。
これらの文字列は、オブジェクトの`__doc__`メンバーを介して自動的に抽出でき、`pydoc`によって使用されます。
(モジュールで`pydoc`を実行して、どのように表示されるかを確認してください。)
docstringには常に3つの二重引用符`"""`形式を使用します（[PEP-257](https://www.google.com/url?sa=D&q=http://www.python.org/dev/peps/pep-0257/)に準拠）。
docstringは要約行（80文字を超えない1つの物理行として編成する必要があります。
ピリオド、疑問符、または感嘆符で終了します。
さらに書き込む場合（推奨）、この後に空白行を続け、その後に最初の行の最初の引用符と同じカーソル位置から始まる残りのdocstringを続ける必要があります。
以下にdocstringのフォーマットガイドラインがあります。

<a id="s3.8.2-comments-in-modules"></a>
<a id="382-modules"></a>
<a id="comments-in-modules"></a>

<a id="module-docs"></a>

#### 3.8.2 Modules

すべてのファイルには、ライセンスの定型文が含まれている必要があります。
プロジェクトで使用されるライセンスに適切なボイラープレートを選択しますたとえば、Apache2.0、BSD、LGPL、GPL）

ファイルは、モジュールの内容と使用法を説明するdocstringで始まる必要があります。

```python
"""A one line summary of the module or program, terminated by a period.

Leave one blank line.  The rest of this docstring should contain an
overall description of the module or program.  Optionally, it may also
contain a brief description of exported classes and functions and/or usage
examples.

  Typical usage example:

  foo = ClassFoo()
  bar = foo.FunctionBar()
"""
```

<a id="s3.8.3-functions-and-methods"></a>
<a id="383-functions-and-methods"></a>
<a id="functions-and-methods"></a>

<a id="function-docs"></a>

#### 3.8.3 Functions and Methods

このセクションでは、"function"は、メソッド、関数、またはジェネレーターを意味します。

次のすべての基準を満たさない限り、関数にはdocstringが必要です。

- 外部からは見えない
- とても短い
- 明らか

docstringは、関数のコードを読み取らずに関数の呼び出しを書き込むのに十分な情報を提供する必要があります。
docstringは、命令型(`"""Fetches rows from a Bigtable."""`)ではなく、
記述型(`"""Fetch rows from a Bigtable."""`)にする必要があります。
ただし、`@property` データ記述子には <a href="#384-classes">same style as attributes</a> が必要です。
docstringは実装ではなく、関数の呼び出し構文とそのセマンティクスを記述する必要があります。
トリッキーなコードの場合、docstringを使用するよりも、コードの横にコメントを付ける方が適切です。

基本クラスのメソッドをオーバーライドするメソッドには、 `"""See base class."""`など、オーバーライドされたメソッドのdocstringにリーダーを送信する単純なdocstringが含まれる場合があります。
理論的根拠は、基本メソッドのdocstringにすでに存在するドキュメントを多くの場所で繰り返す必要がないということです。
ただし、オーバーライドするメソッドの動作がオーバーライドされるメソッドと大幅に異なる場合、または詳細を提供する必要がある場合（たとえば、追加の副作用を文書化する）、オーバーライドするメソッドには少なくともそれらの違いがあるdocstringが必要です。

関数の特定の側面は、以下にリストされている特別なセクションに文書化する必要があります。
各セクションは見出し行で始まり、コロンで終わります。見出し以外のすべてのセクションは、2つまたは4つのスペースのぶら下げインデントを維持する必要があります（ファイル内で一貫している必要があります）。
関数の名前と署名が十分に有益であり、1行のdocstringを使用して適切に記述できる場合は、これらのセクションを省略できます。

<a id="doc-function-args"></a>
[*Args:*](#doc-function-args)
:   各パラメーターを名前でリストします。
説明は名前の後に続き、コロンとそれに続くスペースまたは改行で区切る必要があります。
説明が長すぎて1行の80文字に収まらない場合は、パラメーター名より2〜4スペース大きいぶら下げインデントを使用します（ファイル内の残りのdocstringと一致させてください）。
コードに対応する型注釈が含まれていない場合は、説明に必要な型を含める必要があります。
関数が `*foo`（可変長引数リストおよび/または `**bar`（任意のキーワード引数）を受け入れる場合、それらは `*foo` および `**bar` としてリストされる必要があります。

<a id="doc-function-returns"></a>
[*Returns:* (or *Yields:* for generators)](#doc-function-returns)
:   戻り値のタイプとセマンティクスを説明します。関数がNoneのみを返す場合、このセクションは必要ありません。
docstringがReturnsまたはYieldsで始まり例：`"""Returns row from Bigtable as a tuple of strings."""`）、開始文が戻り値を説明するのに十分な場合も省略できます。

<a id="doc-function-raises"></a>
[*Raises:*](#doc-function-raises)
:   インターフェイスに関連するすべての例外をリストし、その後に説明を続けます。
Args：で説明されているように、同様の例外名+コロン+スペースまたは改行とぶら下げインデントスタイルを使用します。
docstringで指定されたAPIに違反した場合に発生する例外を文書化しないでください
（逆説的に、APIのAPI部分に違反すると動作するため）。

```python
def fetch_smalltable_rows(table_handle: smalltable.Table,
                          keys: Sequence[Union[bytes, str]],
                          require_all_keys: bool = False,
) -> Mapping[bytes, Tuple[str]]:
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle.  String keys will be UTF-8 encoded.

    Args:
        table_handle: An open smalltable.Table instance.
        keys: A sequence of strings representing the key of each table
          row to fetch.  String keys will be UTF-8 encoded.
        require_all_keys: Optional; If require_all_keys is True only
          rows with values set for all keys will be returned.

    Returns:
        A dict mapping keys to the corresponding table row data
        fetched. Each row is represented as a tuple of strings. For
        example:

        {b'Serak': ('Rigel VII', 'Preparer'),
         b'Zim': ('Irk', 'Invader'),
         b'Lrrr': ('Omicron Persei 8', 'Emperor')}

        Returned keys are always bytes.  If a key from the keys argument is
        missing from the dictionary, then that row was not found in the
        table (and require_all_keys must have been False).

    Raises:
        IOError: An error occurred accessing the smalltable.
    """
```

同様に、`Args`のこのバリエーション：改行ありも許可されます：

```python
def fetch_smalltable_rows(table_handle: smalltable.Table,
                          keys: Sequence[Union[bytes, str]],
                          require_all_keys: bool = False,
) -> Mapping[bytes, Tuple[str]]:
    """Fetches rows from a Smalltable.

    Retrieves rows pertaining to the given keys from the Table instance
    represented by table_handle.  String keys will be UTF-8 encoded.

    Args:
      table_handle:
        An open smalltable.Table instance.
      keys:
        A sequence of strings representing the key of each table row to
        fetch.  String keys will be UTF-8 encoded.
      require_all_keys:
        Optional; If require_all_keys is True only rows with values set
        for all keys will be returned.

    Returns:
      A dict mapping keys to the corresponding table row data
      fetched. Each row is represented as a tuple of strings. For
      example:

      {b'Serak': ('Rigel VII', 'Preparer'),
       b'Zim': ('Irk', 'Invader'),
       b'Lrrr': ('Omicron Persei 8', 'Emperor')}

      Returned keys are always bytes.  If a key from the keys argument is
      missing from the dictionary, then that row was not found in the
      table (and require_all_keys must have been False).

    Raises:
      IOError: An error occurred accessing the smalltable.
    """
```

<a id="s3.8.4-comments-in-classes"></a>
<a id="384-classes"></a>
<a id="comments-in-classes"></a>

<a id="class-docs"></a>

#### 3.8.4 Classes

クラスには、クラスを説明するクラス定義の下にdocstringが必要です。
クラスにパブリック属性がある場合、それらはここの`Attributes`セクションに文書化され、[function's `Args`](#doc-function-args)セクションと同じフォーマットに従う必要があります。

```python
class SampleClass:
    """Summary of class here.

    Longer class information....
    Longer class information....

    Attributes:
        likes_spam: A boolean indicating if we like SPAM or not.
        eggs: An integer count of the eggs we have laid.
    """

    def __init__(self, likes_spam=False):
        """Inits SampleClass with blah."""
        self.likes_spam = likes_spam
        self.eggs = 0

    def public_method(self):
        """Performs operation blah."""
```

<a id="s3.8.5-block-and-inline-comments"></a>
<a id="comments-in-block-and-inline"></a>
<a id="s3.8.5-comments-in-block-and-inline"></a>
<a id="385-block-and-inline-comments"></a>

<a id="comments"></a>

#### 3.8.5 Block and Inline Comments

コメントを付ける最後の場所は、コードのトリッキーな部分です。次の [code review](http://en.wikipedia.org/wiki/Code_review)で説明する必要がある場合は、今すぐコメントする必要があります。
複雑な操作は、操作が開始される前に数行のコメントを受け取ります。
自明でないものは、行の終わりにコメントを受け取ります。

```python
# We use a weighted dictionary search to find out where i is in
# the array.  We extrapolate position based on the largest num
# in the array and the array size and then do binary search to
# get the exact number.

if i & (i-1) == 0:  # True if i is 0 or a power of 2.
```

読みやすさを向上させるために、これらのコメントは、コメント文字 `#` でコードから少なくとも2スペース離れて開始し、コメント自体のテキストの前に少なくとも1スペースが続く必要があります。

一方、コードを記述しないでください。
コードを読んでいる人は、Pythonを（あなたがやろうとしていることではありませんが）あなたよりもよく知っていると仮定します。

```python
# BAD COMMENT: Now go through the b array and make sure whenever i occurs
# the next element is i+1
```

<!-- The next section is copied from the C++ style guide. -->

<a id="s3.8.6-punctuation-spelling-and-grammar"></a>
<a id="386-punctuation-spelling-and-grammar"></a>
<a id="spelling"></a>
<a id="punctuation"></a>
<a id="grammar"></a>

<a id="punctuation-spelling-grammar"></a>

#### 3.8.6 Punctuation, Spelling, and Grammar

句読点、スペル、および文法に注意してください。
よく書かれたコメントは、よく書かれていないコメントよりも読みやすいです。

コメントは、適切な大文字と句読点を使用して、説明テキストと同じくらい読みやすくする必要があります。
多くの場合、完全な文は文の断片よりも読みやすくなります。
コード行の最後のコメントなど、短いコメントは形式的でない場合がありますが、スタイルに一貫性を持たせる必要があります。

セミコロンを使用する必要があるときにコンマを使用していることをコードレビューアに指摘させるのはイライラするかもしれませんが、ソースコードが高レベルの明快さと読みやすさを維持することは非常に重要です。
適切な句読点、スペル、および文法は、その目標に役立ちます。

<a id="s3.10-strings"></a>
<a id="310-strings"></a>

<a id="strings"></a>

### 3.10 Strings

パラメータがすべて文字列の場合でも、文字列の書式設定には、[f-string](https://docs.python.org/3/reference/lexical_analysis.html#f-strings)、`%`演算子、または`format`メソッドを使用します。
ただし、最善の判断を使用して、`+`と`%`（または形式）のどちらかを決定してください。
純粋な連結には`%`または`format`メソッドを使用しないでください。

```python
Yes: x = a + b
     x = '%s, %s!' % (imperative, expletive)
     x = '{}, {}'.format(first, second)
     x = 'name: %s; score: %d' % (name, n)
     x = 'name: {}; score: {}'.format(name, n)
     x = f'name: {name}; score: {n}'
```

```python
No: x = '%s%s' % (a, b)  # use + in this case
    x = '{}{}'.format(a, b)  # use + in this case
    x = first + ', ' + second
    x = 'name: ' + name + '; score: ' + str(n)
```

`+` および `+=` 演算子を使用して、ループ内に文字列を累積することは避けてください。
条件によっては、加算を使用して文字列を累積すると、実行時間が線形ではなく2次になる場合があります。
この種の一般的な累積はCPythonで最適化される可能性がありますが、それは実装の詳細です。
最適化が適用される条件は、予測が容易ではなく、変更される可能性があります。
代わりに、各サブ文字列をリストに追加し、ループの終了後に `''.join` をリストに追加するか、各サブ文字列を `io.StringIO` バッファーに書き込みます。
これらの手法は、一貫して償却線形の実行時間の複雑さを持っています。

```python
Yes: items = ['<table>']
     for last_name, first_name in employee_list:
         items.append('<tr><td>%s, %s</td></tr>' % (last_name, first_name))
     items.append('</table>')
     employee_table = ''.join(items)
```

```python
No: employee_table = '<table>'
    for last_name, first_name in employee_list:
        employee_table += '<tr><td>%s, %s</td></tr>' % (last_name, first_name)
    employee_table += '</table>'
```

ファイル内の文字列引用文字の選択と一致してください。
`'` または `"` を選択し、それを使用します。
文字列内で `\\` エスケープする必要がないように、文字列で他の引用文字を使用してもかまいません。

```python
Yes:
  Python('Why are you hiding your eyes?')
  Gollum("I'm scared of lint errors.")
  Narrator('"Good!" thought a happy Python reviewer.')
```

```python
No:
  Python("Why are you hiding your eyes?")
  Gollum('The lint. It burns. It burns us.')
  Gollum("Always the great lint. Watching. Watching.")
```

`'''` よりも複数行の文字列には `"""` を優先します。
プロジェクトは、通常の文字列にも `'` を使用する場合に限り、すべての非docstring複数行文字列に `'''` を使用することを選択できます。
Docstringは `"""` を使用する必要があります。関係なく。

複数行の文字列は、プログラムの残りの部分のインデントとともに流れません。
文字列に余分なスペースを埋め込まないようにする必要がある場合は、連結された1行の文字列または[`textwrap.dedent()`](https://docs.python.org/3/library/textwrap.html#textwrap.dedent)を使用した複数行の文字列を使用して、各行の最初のスペースを削除します。

```python
  No:
  long_string = """This is pretty ugly.
Don't do this.
"""
```

```python
  Yes:
  long_string = """This is fine if your use case can accept
      extraneous leading spaces."""
```

```python
  Yes:
  long_string = ("And this is fine if you cannot accept\n" +
                 "extraneous leading spaces.")
```

```python
  Yes:
  long_string = ("And this too is fine if you cannot accept\n"
                 "extraneous leading spaces.")
```

```python
  Yes:
  import textwrap

  long_string = textwrap.dedent("""\
      This is also fine, because textwrap.dedent()
      will collapse common leading spaces in each line.""")
```

<a id="s3.10.1-logging"></a>
<a id="3101-logging"></a>
<a id="logging"></a>

<a id="logging"></a>

#### 3.10.1 Logging

最初の引数としてパターン文字列％-placeholdersを含む）を期待するロギング関数の場合：
常に最初の引数として文字列リテラル（f文字列ではありません！を使用し、後続の引数としてpattern-parametersを使用して呼び出します。
一部のロギング実装は、展開されていないパターン文字列をクエリ可能なフィールドとして収集します。
また、ロガーが出力するように構成されていないメッセージのレンダリングに時間を費やすことを防ぎます。

```python
  Yes:
  import tensorflow as tf
  logger = tf.get_logger()
  logger.info('TensorFlow Version is: %s', tf.__version__)
```

```python
  Yes:
  import os
  from absl import logging

  logging.info('Current $PAGER is: %s', os.getenv('PAGER', default=''))

  homedir = os.getenv('HOME')
  if homedir is None or not os.access(homedir, os.W_OK):
    logging.error('Cannot write to home directory, $HOME=%r', homedir)
```

```python
  No:
  import os
  from absl import logging

  logging.info('Current $PAGER is:')
  logging.info(os.getenv('PAGER', default=''))

  homedir = os.getenv('HOME')
  if homedir is None or not os.access(homedir, os.W_OK):
    logging.error(f'Cannot write to home directory, $HOME={homedir!r}')
```

<a id="s3.10.2-error-messages"></a>
<a id="3102-error-messages"></a>
<a id="error-messages"></a>

<a id="error-messages"></a>

#### 3.10.2 Error Messages

エラーメッセージ（`ValueError` などの例外のメッセージ文字列やユーザーに表示されるメッセージなど）は、次の3つのガイドラインに従う必要があります。

1. メッセージは、実際のエラー状態と正確に一致する必要があります。
1. 補間されたピースは、常にそのように明確に識別できる必要があります。
1. 単純な自動処理（greppingなど）を許可する必要があります。

```python
  Yes:
  if not 0 <= p <= 1:
    raise ValueError(f'Not a probability: {p!r}')

  try:
    os.rmdir(workdir)
  except OSError as error:
    logging.warning('Could not remove directory (reason: %r): %r',
                    error, workdir)
```

```python
  No:
  if p < 0 or p > 1:  # PROBLEM: also false for float('nan')!
    raise ValueError(f'Not a probability: {p!r}')

  try:
    os.rmdir(workdir)
  except OSError:
    # PROBLEM: Message makes an assumption that might not be true:
    # Deletion might have failed for some other reason, misleading
    # whoever has to debug this.
    logging.warning('Directory already was deleted: %s', workdir)

  try:
    os.rmdir(workdir)
  except OSError:
    # PROBLEM: The message is harder to grep for than necessary, and
    # not universally non-confusing for all possible values of `workdir`.
    # Imagine someone calling a library function with such code
    # using a name such as workdir = 'deleted'. The warning would read:
    # "The deleted directory could not be deleted."
    logging.warning('The %s directory could not be deleted.', workdir)
```

<a id="s3.11-files-and-sockets"></a>
<a id="311-files-and-sockets"></a>
<a id="files-and-sockets"></a>

<a id="files"></a>

### 3.11 Files and Sockets

ファイルとソケットを使い終わったら、それらを明示的に閉じます。

ファイル、ソケット、またはその他のファイルのようなオブジェクトを不必要に開いたままにしておくと、多くの欠点：

- それらは、ファイル記述子などの限られたシステムリソースを消費する可能性があります。
  このようなオブジェクトの多くを処理するコードは、使用後すぐにシステムに戻されない場合、これらのリソースを不必要に使い果たす可能性があります。
- ファイルを開いたままにしておくと、ファイルの移動や削除などの他のアクションが妨げられる可能性があります。
- プログラム全体で共有されているファイルとソケットは、論理的に閉じられた後、誤って読み取りまたは書き込みが行われる可能性があります。
  それらが実際に閉じられている場合、それらからの読み取りまたは書き込みを試みると例外がスローされ、問題がより早く認識されます。

さらに、ファイルオブジェクトが破棄されると、ファイルとソケットは自動的に閉じられますが、ファイルオブジェクトの存続期間をファイルの状態に関連付けることはお勧めできません。

- ランタイムが実際にファイルのデストラクタを実行する時期についての保証はありません。
  さまざまなPython実装は、遅延ガベージコレクションなど、さまざまなメモリ管理手法を使用します。
  これにより、オブジェクトの寿命が任意に無期限に長くなる可能性があります。
- ファイルへの予期しない参照。
  例： グローバルまたは例外トレースバックでは、意図したよりも長く保持される場合があります。

ファイルを管理するための推奨される方法は、[`with` statement](http://docs.python.org/reference/compound_stmts.html#the-with-statement)を使用することです。

```python
with open("hello.txt") as hello_file:
    for line in hello_file:
        print(line)
```

`with` ステートメントをサポートしないファイルのようなオブジェクトの場合は、`contextlib.closeing()` を使用します。

```python
import contextlib

with contextlib.closing(urllib.urlopen("http://www.python.org/")) as front_page:
    for line in front_page:
        print(line)
```

<a id="s3.12-todo-comments"></a>
<a id="312-todo-comments"></a>

<a id="todo"></a>

### 3.12 TODO Comments

一時的、短期的な解決策、または十分であるが完全ではないコードには、`TODO` コメントを使用します。

`TODO` コメントは、すべて大文字の文字列 `TODO` と、括弧で囲まれた名前、電子メールアドレス、または問題に関する最適なコンテキストでの個人または問題のその他の識別子で始まります。
続いて、何をすべきかについて説明します。

目的は、詳細を取得する方法を見つけるために検索できる一貫した `TODO` 形式を用意することです。
`TODO` は、参照された人が問題を修正するという約束ではありません。
したがって、`TODO` を作成するとき、ほとんどの場合、名前が付けられます。

```python
# TODO(kl@gmail.com): Use a "*" here for string repetition.
# TODO(Zeke) Change this to use relations.
```

`TODO` が「将来の日付で何かを行う」という形式の場合は、非常に具体的な日付（"2009年11月までに修正"）または非常に具体的なイベント（"すべてのクライアントがXML応答を処理できるときにこのコードを削除する"）を含めるようにしてください。

<a id="s3.13-imports-formatting"></a>
<a id="313-imports-formatting"></a>

<a id="imports-formatting"></a>

### 3.13 Imports formatting

インポートは別々の行に行う必要があります。インポートの入力には例外があります( [exceptions for `typing` imports](#typing-imports))。

E.g.:

```python
Yes: import os
     import sys
     from typing import Mapping, Sequence
```

```python
No:  import os, sys
```

インポートは、モジュールのコメントとdocstringの直後、モジュールのグローバル変数と定数の前に、常にファイルの先頭に配置されます。
インポートは、最も一般的なものから最も一般的でないものへとグループ化する必要があります。

1. Pythonの将来のインポートステートメント。 例えば：

    ```python
    from __future__ import absolute_import
    from __future__ import division
    from __future__ import print_function
    ```

    それらの詳細については、[上記](#from-future-imports)を参照してください。

1. Python標準ライブラリのインポート。 例えば：

    ```python
    import sys
    ```

1. [third-party](https://pypi.org/)のモジュールまたはパッケージのインポート。 例えば：

    ```python
    import tensorflow as tf
    ```

1. コードリポジトリサブパッケージのインポート。例えば：

    ```python
    from otherproject.ai import mind
    ```

1. **非推奨**：このファイルと同じトップレベルのサブパッケージの一部であるアプリケーション固有のインポート。例えば：

    ```python
    from myproject.backend.hgwells import time_machine
    ```

    これを行う古いGooglePythonスタイルのコードを見つけるかもしれませんが、それはもはや必要ではありません。
    **新しいコードはこれを気にしないことをお勧めします**。
    アプリケーション固有のサブパッケージのインポートを他のサブパッケージのインポートと同じように扱うだけです。

各グループ内で、インポートは、各モジュールの完全なパッケージパス`パスインポートからのパス...`に従って、大文字と小文字を区別せずに辞書式に並べ替える必要があります。
コードは、オプションでインポートセクションの間に空白行を配置できます。

```python
import collections
import queue
import sys

from absl import app
from absl import flags
import bs4
import cryptography
import tensorflow as tf

from book.genres import scifi
from myproject.backend import huxley
from myproject.backend.hgwells import time_machine
from myproject.backend.state_machine import main_loop
from otherproject.ai import body
from otherproject.ai import mind
from otherproject.ai import soul

# Older style code may have these imports down here instead:
#from myproject.backend.hgwells import time_machine
#from myproject.backend.state_machine import main_loop
```

<a id="s3.14-statements"></a>
<a id="314-statements"></a>

<a id="statements"></a>

### 3.14 Statements

通常、1行に1つのステートメントのみ。

ただし、ステートメント全体が1行に収まる場合にのみ、テストの結果をテストと同じ行に配置できます。
特に、`try`/`except`を使用してこれを行うことはできません。
これは、`try`と`except`の両方を同じ行に収めることができないためです。
また、`他にない場合にのみ`、`try`/`except`を使用して行うことができます。

```python
Yes:

  if foo: bar(foo)
```

```python
No:

  if foo: bar(foo)
  else:   baz(foo)

  try:               bar(foo)
  except ValueError: baz(foo)

  try:
      bar(foo)
  except ValueError: baz(foo)
```

<a id="s3.15-accessors"></a>
<a id="s3.15-access-control"></a>
<a id="315-access-control"></a>
<a id="access-control"></a>

<a id="accessors"></a>

### 3.15 Accessors

アクセサ関数が簡単な場合は、アクセサ関数の代わりにパブリック変数を使用して、Pythonでの関数呼び出しの余分なコストを回避する必要があります。
さらに機能が追加されると、`property`を使用して構文の一貫性を保つことができます。

一方、アクセスがより複雑な場合、または変数へのアクセスのコストが大きい場合は、`get_foo()`や`set_foo()`などの関数呼び出し[Naming](#s3.16-naming)ガイドラインに従う）を使用する必要があります。
過去の動作でプロパティを介したアクセスが許可されていた場合は、新しいアクセサ関数をプロパティにバインドしないでください。
古い方法で変数にアクセスしようとしているコードは、複雑さの変化を認識できるように、目に見えて壊れているはずです。

<a id="s3.16-naming"></a>
<a id="316-naming"></a>

<a id="naming"></a>

### 3.16 Naming

`module_name`, `package_name`, `ClassName`, `method_name`, `ExceptionName`,
`function_name`, `GLOBAL_CONSTANT_NAME`, `global_var_name`, `instance_var_name`,
`function_parameter_name`, `local_var_name`.

関数名、変数名、およびファイル名は説明的である必要があります。
略語を避けます。
特に、プロジェクト外の読者にはあいまいまたはなじみのない略語を使用しないでください。
また、単語内の文字を削除して略語を使用しないでください。

常に `.py` ファイル名拡張子を使用してください。
ダッシュは絶対に使用しないでください。

<a id="s3.16.1-names-to-avoid"></a>
<a id="3161-names-to-avoid"></a>

<a id="names-to-avoid"></a>

#### 3.16.1 Names to Avoid (避けるべき名前)

- 特に許可されている以下の場合を除いて、単一文字の名前：

  - カウンターまたはイテレーター (例えば. `i`, `j`, `k`, `v`, et al.)
  - `e` は`try/except`ステートメントの例外識別子として使用します。
  - `with`ステートメントのファイルハンドルとしての `f`

  1文字の命名を乱用しないように注意してください。
  一般的に言えば、説明性は名前の可視性の範囲に比例する必要があります。
  たとえば、`i` は5行のコードブロックの良い名前かもしれませんが、複数のネストされたスコープ内では、あいまいすぎる可能性があります。

- パッケージ/モジュール名のダッシュ（`-`）
- `__double_leading_and_trailing_underscore__` names （Pythonで予約済み）
- 不快な用語
- 変数のタイプを不必要に含む名前（例：`id_to_name_dict`）

<a id="s3.16.2-naming-conventions"></a>
<a id="3162-naming-convention"></a>

<a id="naming-conventions"></a>

#### 3.16.2 Naming Conventions (命名規則)

- "Internal"とは、モジュールの内部、またはクラス内で保護またはプライベートを意味します。
- 単一の下線（`_`）を前に付けると、モジュール変数と関数を保護するためのサポートがいくつかあります（リンターは保護されたメンバーのアクセスにフラグを立てます）。
  インスタンス変数またはメソッドの前に二重アンダースコア（`__`別名"dunder"）を付けると、変数またはメソッドがそのクラスに対してプライベートになります（名前マングリングを使用）。
  読みやすさとテスト容易性に影響を与え、実際には非公開ではないため、使用をお勧めしません。
- 関連するクラスとトップレベルの関数を一緒にモジュールに配置します。
  Javaとは異なり、モジュールごとに1つのクラスに制限する必要はありません。
- クラス名にはCapWordsを使用しますが、モジュール名にはlower\_with\_under.pyを使用します。
  CapWords.pyという名前の古いモジュールがいくつかありますが、モジュールがクラスにちなんで名付けられたときに混乱するため、これは現在推奨されていません。
  （ちょっとまって-`import StringIO`を記述しましたか、それとも`from StringIO import StringIO`を記述しましたか？）
- それらのコンポーネントがCapWordsを使用している場合でも、名前の論理コンポーネントを区切るために、`test`で始まるunittestメソッド名にアンダースコアが表示される場合があります。
  考えられるパターンの1つは、`test<MethodUnderTest>_<state>`です。
  たとえば、`testPop_EmptyStack`は問題ありません。
  テストメソッドに名前を付ける正しい方法は1つではありません。

<a id="s3.16.3-file-naming"></a>
<a id="3163-file-naming"></a>

<a id="file-naming"></a>

#### 3.16.3 File Naming (ファイルの命名)

Pythonファイル名には`.py`拡張子を付ける必要があり、ダッシュ（`-`）を含めることはできません。
これにより、それらをインポートしてユニットテストすることができます。
実行可能ファイルに拡張子なしでアクセスできるようにする場合は、シンボリックリンクまたは`exec "$0.py" "$@"`を含む単純なbashラッパーを使用します。

<a id="s3.16.4-guidelines-derived-from-guidos-recommendations"></a>
<a id="3164-guidelines-derived-from-guidos-recommendations"></a>

<a id="guidelines-derived-from-guidos-recommendations"></a>

#### 3.16.4 Guidelines derived from [Guido](https://en.wikipedia.org/wiki/Guido_van_Rossum)'s Recommendations

<table rules="all" border="1" summary="Guidelines from Guido's Recommendations"
       cellspacing="2" cellpadding="2">

  <tr>
    <th>Type</th>
    <th>Public</th>
    <th>Internal</th>
  </tr>

  <tr>
    <td>Packages</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Modules</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code></td>
  </tr>

  <tr>
    <td>Classes</td>
    <td><code>CapWords</code></td>
    <td><code>_CapWords</code></td>
  </tr>

  <tr>
    <td>Exceptions</td>
    <td><code>CapWords</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Functions</td>
    <td><code>lower_with_under()</code></td>
    <td><code>_lower_with_under()</code></td>
  </tr>

  <tr>
    <td>Global/Class Constants</td>
    <td><code>CAPS_WITH_UNDER</code></td>
    <td><code>_CAPS_WITH_UNDER</code></td>
  </tr>

  <tr>
    <td>Global/Class Variables</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code></td>
  </tr>

  <tr>
    <td>Instance Variables</td>
    <td><code>lower_with_under</code></td>
    <td><code>_lower_with_under</code> (protected)</td>
  </tr>

  <tr>
    <td>Method Names</td>
    <td><code>lower_with_under()</code></td>
    <td><code>_lower_with_under()</code> (protected)</td>
  </tr>

  <tr>
    <td>Function/Method Parameters</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

  <tr>
    <td>Local Variables</td>
    <td><code>lower_with_under</code></td>
    <td></td>
  </tr>

</table>

<a id="s3.17-main"></a>
<a id="317-main"></a>

<a id="main"></a>

### 3.17 Main

Pythonでは、`pydoc` と単体テストでモジュールをインポート可能にする必要があります。
ファイルが実行可能ファイルとして使用されることを意図している場合、その主な機能は  `main()` 関数にある必要があり、
コードはメインプログラムを実行する前に常に `if __name__ == '__main__'` をチェックする必要があります。
モジュールがインポートされます。

[absl](https://github.com/abseil/abseil-py) を使用する場合は、`app.run` を使用します。

```python
from absl import app
...

def main(argv):
    # process non-flag arguments
    ...

if __name__ == '__main__':
    app.run(main)
```

それ以外の場合は、次を使用します。

```python
def main():
    ...

if __name__ == '__main__':
    main()
```

モジュールがインポートされると、トップレベルのすべてのコードが実行されます。
関数を呼び出したり、オブジェクトを作成したり、ファイルが `pydoc` されているときに実行してはならないその他の操作を実行したりしないように注意してください。

<a id="s3.18-function-length"></a>
<a id="318-function-length"></a>

<a id="function-length"></a>

### 3.18 Function length (関数の長さ)

小さくて焦点を絞った機能を好む。

長い関数が適切な場合があることを認識しているため、関数の長さに厳しい制限はありません。
関数が約40行を超える場合は、プログラムの構造を損なうことなく分割できるかどうかを検討してください。

長い関数が完全に機能するようになったとしても、数か月以内に誰かがそれを変更すると、新しい動作が追加される可能性があります。
これにより、見つけるのが難しいバグが発生する可能性があります。
関数を短くシンプルに保つことで、他の人がコードを読んだり変更したりしやすくなります。

一部のコードを操作すると、長くて複雑な関数が見つかる可能性があります。
既存のコードを変更することを恐れないでください。
そのような関数の操作が難しいことがわかった場合、エラーのデバッグが難しい場合、またはその一部をいくつかの異なるコンテキストで使用したい場合は、関数をより小さなものに分割することを検討してください。
そしてより扱いやすい部分。

<a id="s3.19-type-annotations"></a>
<a id="319-type-annotations"></a>

<a id="type-annotations"></a>

### 3.19 Type Annotations (タイプ注釈)

<a id="s3.19.1-general-rules"></a>
<a id="s3.19.1-general"></a>
<a id="3191-general-rules"></a>

<a id="typing-general"></a>

#### 3.19.1 General Rules (一般的なルール)

- [PEP-484](https://www.python.org/dev/peps/pep-0484/)をよく理解してください。
- メソッドの場合、`cls`か`self`に注釈を付けます。
  例：`@classmethod def create(cls: Type[T]) -> T:return cls()`
- 他の変数または返される型を表現する必要がない場合は、`Any`を使用します。
- モジュール内のすべての関数に注釈を付ける必要はありません。
  - 少なくともパブリックAPIに注釈を付けます。
  - 判断を使用して、一方では安全性と明快さ、他方では柔軟性のバランスをとってください。
  - タイプ関連のエラー（以前のバグや複雑さ）が発生しやすいコードに注釈を付けます。
  - 理解しにくいコードに注釈を付けます。
  - タイプの観点からコードが安定したら、コードに注釈を付けます。多くの場合、柔軟性をあまり失うことなく、成熟したコードのすべての関数に注釈を付けることができます。

<a id="s3.19.2-line-breaking"></a>
<a id="3192-line-breaking"></a>

<a id="typing-line-breaking"></a>

#### 3.19.2 Line Breaking (改行)

既存の [indentation](#indentation) 規則に従うようにしてください。

注釈を付けると、多くの関数シグネチャが"1行に1つのパラメータ"になります。

```python
def my_method(self,
              first_var: int,
              second_var: Foo,
              third_var: Optional[Bar]) -> int:
  ...
```

たとえば、変数名と型注釈の間ではなく、常に変数間で分割することをお勧めします。
ただし、すべてが同じ行に収まる場合は、それを選択してください。

```python
def my_method(self, first_var: int) -> int:
  ...
```

関数名、最後のパラメーター、および戻り値のタイプの組み合わせが長すぎる場合は、新しい行で4ずつインデントします。

```python
def my_method(
    self, first_var: int) -> Tuple[MyLongType1, MyLongType1]:
  ...
```

戻りタイプが最後のパラメーターと同じ行に収まらない場合、推奨される方法は、新しい行でパラメーターを4だけインデントし、閉じ括弧を `def` に揃えることです。

```python
Yes:
def my_method(
    self, other_arg: Optional[MyLongType]
) -> Dict[OtherLongType, MyLongType]:
  ...
```

`pylint` を使用すると、閉じ括弧を新しい行に移動して、開始括弧に揃えることができますが、これは読みにくくなります。

```python
No:
def my_method(self,
              other_arg: Optional[MyLongType]
             ) -> Dict[OtherLongType, MyLongType]:
  ...
```

上記の例のように、型を壊さないことを好みます。
ただし、長すぎて1行にできない場合もあります（サブタイプを壊さないようにしてください）。

```python
def my_method(
    self,
    first_var: Tuple[List[MyLongType1],
                     List[MyLongType2]],
    second_var: List[Dict[
        MyLongType3, MyLongType4]]) -> None:
  ...
```

単一の名前とタイプが長すぎる場合は、タイプに [alias](#typing-aliases) を使用することを検討してください。
最後の手段は、コロンの後で中断し、4でインデントすることです。

```python
Yes:
def my_function(
    long_variable_name:
        long_module_name.LongTypeName,
) -> None:
  ...
```

```python
No:
def my_function(
    long_variable_name: long_module_name.
        LongTypeName,
) -> None:
  ...
```

<a id="s3.19.3-forward-declarations"></a>
<a id="3193-forward-declarations"></a>

<a id="forward-declarations"></a>

#### 3.19.3 Forward Declarations (前方宣言)

まだ定義されていない同じモジュールのクラス名を使用する必要がある場合（たとえば、クラス宣言内にクラスが必要な場合、または以下で定義されているクラスを使用する場合）、クラス名に文字列を使用します。

```python
class MyClass:

  def __init__(self,
               stack: List["MyClass"]) -> None:
```

<a id="s3.19.4-default-values"></a>
<a id="3194-default-values"></a>

<a id="typing-default-values"></a>

#### 3.19.4 Default Values (デフォルト値)

[PEP-008](https://www.python.org/dev/peps/pep-0008/#other-recommendations)に従い、
`=` の前後にスペースを使用するのは、型注釈とデフォルト値の両方を持つ引数_のみ_です。

```python
Yes:
def func(a: int = 0) -> int:
  ...
```

```python
No:
def func(a:int=0) -> int:
  ...
```

<a id="s3.19.5-nonetype"></a>
<a id="s3.19.5-none-type"></a>
<a id="3195-nonetype"></a>

<a id="none-type"></a>

#### 3.19.5 NoneType

Python型システムでは、`NoneType`は"first class"型であり、入力の目的では、`None`は`NoneType`のエイリアスです。
引数が`None`になる可能性がある場合は、宣言する必要があります。`Union`を使用できますが、他にタイプが1つしかない場合は、`Optional`を使用してください。

暗黙の`Optional`ではなく、明示的な`Optional`を使用します。
以前のバージョンのPEP-484では、`a: Text = None` を `a: Optional[Text] = None` として解釈できましたが、これは推奨される動作ではなくなりました。

```python
Yes:
def func(a: Optional[Text], b: Optional[Text] = None) -> Text:
  ...
def multiple_nullable_union(a: Union[None, Text, int]) -> Text
  ...
```

```python
No:
def nullable_union(a: Union[None, Text]) -> Text:
  ...
def implicit_optional(a: Text = None) -> Text:
  ...
```

<a id="s3.19.6-type-aliases"></a>
<a id="s3.19.6-aliases"></a>
<a id="3196-type-aliases"></a>
<a id="typing-aliases"></a>

<a id="type-aliases"></a>

#### 3.19.6 Type Aliases

複合型のエイリアスを宣言できます。
エイリアスの名前は大文字である必要があります。
エイリアスがこのモジュールでのみ使用される場合は、\_Privateである必要があります。

たとえば、モジュールの名前とタイプの名前が長すぎる場合：

```python
_ShortName = module_with_long_name.TypeWithLongName
ComplexMap = Mapping[Text, List[Tuple[int, int]]]
```

他の例は、複雑なネストされた型と関数からの複数の戻り変数（タプルとして）です。

<a id="s3.19.7-ignoring-types"></a>
<a id="s3.19.7-ignore"></a>
<a id="3197-ignoring-types"></a>

<a id="typing-ignore"></a>

#### 3.19.7 Ignoring Types (タイプを無視する)

特別なコメントがある行の型チェックを無効にすることができます
`# type:ignore`.

`pytype` には、特定のエラーに対する無効化オプションがあります（lintと同様）。

```python
# pytype: disable=attribute-error
```

<a id="s3.19.8-typing-variables"></a>
<a id="s3.19.8-comments"></a>
<a id="3198-typing-internal-variables"></a>

<a id="typing-variables"></a>

#### 3.19.8 Typing Variables (変数の入力)

内部変数の型が推測しにくい、または不可能な場合は、いくつかの方法でその型を指定できます。

<a id="type-comments"></a>
[*Type Comments:*](#type-comments)
:   `# type:`を使う 行末にコメント

```python
a = SomeUndecoratedFunction()  # type: Foo
```

<a id="annotated-assignments"></a>
[*Annotated Assignments*](#annotated-assignments)
:   関数の引数と同様に、コロンを使用して変数名と値の間に入力します。

```python
a: Foo = SomeUndecoratedFunction()
```

<a id="s3.19.9-tuples-vs-lists"></a>
<a id="s3.19.9-tuples"></a>
<a id="3199-tuples-vs-lists"></a>

<a id="typing-tuples"></a>

#### 3.19.9 Tuples vs Lists (タプルとリスト)

型付きリストには、単一の型のオブジェクトのみを含めることができます。
型付きタプルは、単一の繰り返し型、または異なる型の要素のセット数のいずれかを持つことができます。
後者は通常、関数からの戻り型として使用されます。

```python
a = [1, 2, 3]  # type: List[int]
b = (1, 2, 3)  # type: Tuple[int, ...]
c = (1, "2", 3.5)  # type: Tuple[int, Text, float]
```

<a id="s3.19.10-typevars"></a>
<a id="s3.19.10-type-var"></a>
<a id="31910-typevar"></a>
<a id="typing-type-var"></a>

<a id="typevars"></a>

#### 3.19.10 TypeVars

Python型システムには [generics](https://www.python.org/dev/peps/pep-0484/#generics)があります。
ファクトリ関数`TypeVar`は、それらを使用する一般的な方法です。

例:

```python
from typing import List, TypeVar
T = TypeVar("T")
...
def next(l: List[T]) -> T:
  return l.pop()
```

TypeVarは制約できます：

```python
AddableType = TypeVar("AddableType", int, float, Text)
def add(a: AddableType, b: AddableType) -> AddableType:
  return a + b
```

`typing` モジュールで一般的に定義されている型変数は `AnyStr` です。
`bytes` または `unicode` であり、すべて同じタイプである必要がある複数の注釈に使用します。

```python
from typing import AnyStr
def check_length(x: AnyStr) -> AnyStr:
  if len(x) <= 42:
    return x
  raise ValueError()
```

<a id="s3.19.11-string-types"></a>
<a id="s3.19.11-strings"></a>
<a id="31911-string-types"></a>

<a id="typing-strings"></a>

#### 3.19.11 String types (文字列タイプ)

文字列に注釈を付けるための適切なタイプは、コードの対象となるPythonのバージョンによって異なります。

Python3のみのコードの場合は、`str` を使用することをお勧めします。
`Text` も使用できます。どちらか一方を一貫して使用してください。

Python2互換コードの場合は、`Text` を使用します。まれに、`str` が意味をなす場合があります。
通常、戻り型が2つのPythonバージョン間で同じでない場合の互換性を支援します。
`Unicode` の使用は避けてください。Python3には存在しません。

この不一致が存在する理由は、`str` がPythonのバージョンによって意味が異なるためです。

```python
No:
def py2_code(x: str) -> unicode:
  ...
```

バイナリデータを処理するコードの場合は、`bytes` を使用します。

```python
def deals_with_binary_data(x: bytes) -> bytes:
  ...
```

テキストデータを処理するPython2互換コード（Python2では`str`または`unicode`、Python3では`str`）の場合は、`Text`を使用します。
Python3の場合、テキストデータを処理するコードのみ、`str`を優先します。

```python
from typing import Text
...
def py2_compatible(x: Text) -> Text:
  ...
def py3_only(x: str) -> str:
  ...
```

タイプがバイトまたはテキストのいずれかである場合は、適切なテキストタイプで `Union` を使用します。

```python
from typing import Text, Union
...
def py2_compatible(x: Union[bytes, Text]) -> Union[bytes, Text]:
  ...
def py3_only(x: Union[bytes, str]) -> Union[bytes, str]:
  ...
```

関数のすべての文字列タイプが常に同じである場合、たとえば、戻りタイプが上記のコードの引数タイプと同じである場合は、
[AnyStr](#typing-type-var) を使用します。

このように書くと、コードをPython3に移植するプロセスが簡素化されます。

<a id="s3.19.12-imports-for-typing"></a>
<a id="s3.19.12-imports"></a>
<a id="31912-imports-for-typing"></a>

<a id="typing-imports"></a>

#### 3.19.12 Imports For Typing

`typing` モジュールのクラスの場合は、常にクラス自体をインポートしてください。
 `typing` モジュールから1行で複数の特定のクラスをインポートすることが明示的に許可されています。例：

```python
from typing import Any, Dict, Optional
```

`typing`からインポートするこの方法ではローカル名前空間にアイテムが追加されるため、`typing` の名前はキーワードと同様に扱われる必要があり、入力されているかどうかに関係なく、Pythonコードで定義されていません。
モジュール内のタイプと既存の名前の間に衝突がある場合は、`import x as y` を使用してインポートします。

```python
from typing import Any as AnyType
```

<a id="s3.19.13-conditional-imports"></a>
<a id="31913-conditional-imports"></a>

<a id="typing-conditional-imports"></a>

#### 3.19.13 Conditional Imports (条件付きインポート)

条件付きインポートは、型チェックに必要な追加のインポートを実行時に回避する必要がある例外的な場合にのみ使用してください。
このパターンは推奨されません。
トップレベルのインポートを許可するようにコードをリファクタリングするなどの代替手段をお勧めします。

型注釈にのみ必要なインポートは、`if TYPE_CHECKING:` ブロック内に配置できます。

- 条件付きでインポートされた型は、アノテーション式が実際に評価されるPython 3.6と上位互換性を保つために、文字列として参照される必要があります。
- ここでは、入力のみに使用されるエンティティのみを定義する必要があります。
  これにはエイリアスが含まれます。
  そうしないと、モジュールが実行時にインポートされないため、実行時エラーになります。
- ブロックは、すべての通常のインポートの直後にある必要があります。
- 入力インポートリストに空の行があってはなりません。
- このリストを通常のインポートリストであるかのように並べ替えます。

```python
import typing
if typing.TYPE_CHECKING:
  import sketch
def f(x: "sketch.Sketch"): ...
```

<a id="s3.19.14-circular-dependencies"></a>
<a id="s3.19.14-circular-deps"></a>
<a id="31914-circular-dependencies"></a>

<a id="typing-circular-deps"></a>

#### 3.19.14 Circular Dependencies (循環依存)

入力によって引き起こされる循環依存は、コードの臭いです。
このようなコードは、リファクタリングに適しています。
技術的には循環依存関係を維持することは可能ですが、各モジュールが他のモジュールに依存する必要があるため、さまざまなビルドシステムではそうすることができません。

循環依存インポートを作成するモジュールを `Any` に置き換えます。
意味のある名前で [alias](#typing-aliases) を設定し、このモジュールの実際のタイプ名を使用します（Anyのany属性はAnyです）。
エイリアス定義は、最後のインポートから1行で区切る必要があります。

```python
from typing import Any

some_mod = Any  # some_mod.py imports this module.
...

def my_method(self, var: "some_mod.SomeType") -> None:
  ...
```

<a id="typing-generics"></a>
<a id="s3.19.15-generics"></a>
<a id="31915-generics"></a>

<a id="generics"></a>

#### 3.19.15 Generics

注釈を付けるときは、ジェネリック型の型パラメーターを指定することをお勧めします。
 それ以外の場合、ジェネリックのパラメータはAnyであると見なされます。
 [the generics' parameters will be assumed to be `Any`](https://www.python.org/dev/peps/pep-0484/#the-any-type)

```python
def get_names(employee_ids: List[int]) -> Dict[int, Any]:
  ...
```

```python
# These are both interpreted as get_names(employee_ids: List[Any]) -> Dict[Any, Any]
def get_names(employee_ids: list) -> Dict:
  ...

def get_names(employee_ids: List) -> Dict:
  ...
```

ジェネリックに最適な型パラメーターが `Any` の場合は、明示的にしますが、多くの場合、[`TypeVar`](#typing-type-var) の方が適切な場合があることに注意してください。

```python
def get_names(employee_ids: List[Any]) -> Dict[Any, Text]:
  """Returns a mapping from employee ID to employee name for given IDs."""
```

```python
T = TypeVar('T')
def get_names(employee_ids: List[T]) -> Dict[T, Text]:
  """Returns a mapping from employee ID to employee name for given IDs."""
```

<a id="4-parting-words"></a>

<a id="consistency"></a>

## 4 Parting Words

*BE CONSISTENT*.

コードを編集している場合は、数分かけて周囲のコードを確認し、そのスタイルを判断してください。
彼らがすべての算術演算子の周りにスペースを使用している場合は、あなたもそうすべきです。
コメントの周りにハッシュマークの小さなボックスがある場合は、コメントの周りにもハッシュマークの小さなボックスを配置します。

スタイルガイドラインを持つことのポイントは、コーディングの共通の語彙を持っていることです。
そうすれば、人々はあなたが言っている方法ではなく、あなたが言っていることに集中できます。
ここではグローバルスタイルのルールを提示して、人々が語彙を理解できるようにしますが、ローカルスタイルも重要です。
ファイルに追加したコードが、そのファイルの周囲にある既存のコードと大幅に異なって見える場合、読者がファイルを読みに行くときにリズムが狂ってしまいます。
これは避けてください。
