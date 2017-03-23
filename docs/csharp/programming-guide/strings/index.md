---
title: "文字列 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 文字列"
  - "文字列 [C#]"
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
caps.latest.revision: 41
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 41
---
# 文字列 (C# プログラミング ガイド)
文字列は、値がテキストである <xref:System.String> 型のオブジェクトです。  内部では、テキストは <xref:System.Char> オブジェクトの順次読み取り専用コレクションとして格納されます。  C\# の文字列の末尾には null 終端文字はありません。したがって、C\# の文字列には任意の数の null 文字 \('\\0'\) を埋め込むことができます。  文字列の <xref:System.String.Length%2A> プロパティは、Unicode 文字の数ではなく、文字列に含まれている `Char` オブジェクトの数を表します。  文字列内の個別の Unicode コード ポイントにアクセスするには、<xref:System.Globalization.StringInfo> オブジェクトを使用します。  
  
## 文字列と System.String  
 C\# では、`string` キーワードは <xref:System.String> のエイリアスです。  したがって、`String` と `string` は等価であり、どちらの名前付け規則を使用してもかまいません。  `String` クラスは、文字列を安全に作成、操作、および比較するためのさまざまなメソッドを提供します。  また、C\# 言語は、一般的な文字列操作を簡略化するためにいくつかの演算子をオーバーロードします。  キーワードの詳細については、「[string](../../../csharp/language-reference/keywords/string.md)」を参照してください。  型およびメソッドの詳細については、「<xref:System.String>」を参照してください。  
  
## 文字列の宣言と初期化  
 次の例に示すように、文字列はさまざまな方法で宣言および初期化できます。  
  
 [!code-cs[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 文字列を文字の配列で初期化する場合を除き、文字列オブジェクトの作成に [new](../../../csharp/language-reference/keywords/new-operator.md) 演算子を使用しないでください。  
  
 文字列の長さが 0 の新しい <xref:System.String> オブジェクトを作成するには、<xref:System.String.Empty> 定数値で文字列を初期化します。  長さ 0 の文字列のリテラル文字列表現は "" です。  [null](../../../csharp/language-reference/keywords/null.md) ではなく <xref:System.String.Empty> 値で文字列を初期化することで、<xref:System.NullReferenceException> が発生する可能性が低くなります。  アクセス前に文字列の値を確認するには、静的な <xref:System.String.IsNullOrEmpty%28System.String%29> メソッドを使用します。  
  
## 文字列オブジェクトの不変性  
 文字列オブジェクトは*変更不可*です。つまり、作成した文字列オブジェクトは変更できません。  文字列を変更するように見える <xref:System.String> メソッドと C\# 演算子はすべて、実際には新しい文字列オブジェクトで結果を返します。  次の例では、`s1` と `s2` の内容を連結して 1 つの文字列を形成するときに、2 つの元の文字列は変更されません。  `+=` 演算子で、連結した内容を含む新しい文字列が作成されます。  新しいオブジェクトは変数 `s1` に代入され、`s1` に代入された元のオブジェクトはガベージ コレクションに対して解放されます。これは、他の変数がこのオブジェクトへの参照を保持していないためです。  
  
 [!code-cs[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 文字列の "変更" では、実際には文字列が新しく作成されるため、文字列への参照を作成するときには注意が必要です。  文字列の参照を作成し、基の文字列を "変更" する場合、参照は文字列が変更されたときに作成された新しいオブジェクトではなく、元のオブジェクトを指したままになります。  この動作を表すコードの例を次に示します。  
  
 [!code-cs[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 元の文字列での検索操作や置換操作などの変更に基づく新しい文字列を作成する方法の詳細については、「[方法 : 文字列の内容を変更する](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md)」を参照してください。  
  
## 標準リテラル文字列と逐語的リテラル文字列  
 次の例に示すように、C\# で提供されるエスケープ文字を埋め込む必要がある場合は、標準リテラル文字列を使用します。  
  
 [!code-cs[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 文字列テキストに円記号が含まれる場合 \(ファイル パスなど\) は、使いやすさと読みやすさを考慮して、逐語的文字列を使用します。  逐語的文字列は、文字列テキストの一部として改行文字を保持するため、複数行文字列の初期化に使用できます。  引用符を逐語的文字列に埋め込むには、二重の引用符を使用します。  逐語的文字列の一般的な使用方法の例を次に示します。  
  
 [!code-cs[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## 文字列のエスケープ シーケンス  
  
|エスケープ シーケンス|文字名|Unicode エンコーディング|  
|-----------------|---------|----------------------|  
|\\'|単一引用符|0x0027|  
|\\"|二重引用符|0x0022|  
|\\\\|円記号|0x005C|  
|\\0|Null|0x0000|  
|\\a|警告|0x0007|  
|\\b|バックスペース|0x0008|  
|\\f|フォーム フィード|0x000C|  
|\\n|改行|0x000A|  
|\\r|キャリッジ リターン|0x000D|  
|\\t|水平タブ。|0x0009|  
|\\U|サロゲート ペアの Unicode エスケープ シーケンス|\\Unnnnnnnn|  
|\\u|Unicode エスケープ シーケンス|\\u0041 \= "A"|  
|\\v|垂直タブ|0x000B|  
|\\x|Unicode エスケープ シーケンス \(可変長である点を除き "\\u" に類似\)|\\x0041 \= "A"|  
  
> [!NOTE]
>  コンパイル時に、逐語的文字列はエスケープ シーケンスと同様に通常の文字列に変換されます。  したがって、逐語的文字列をデバッガーのウォッチ ウィンドウで表示すると、ソース コードの逐語的バージョンではなく、コンパイラが追加したエスケープ文字が表示されます。  たとえば、逐語的文字列 @"C:\\files.txt" は、ウォッチ ウィンドウでは "C:\\\\files.txt" と表示されます。  
  
## 書式指定文字列  
 書式指定文字列は、内容が実行時に動的に決定される文字列です。  静的な <xref:System.String.Format%2A> メソッドを使用して、実行時に他の値に置換されるプレースホルダーを中かっこ内に埋め込むことで、書式指定文字列を作成します。  書式指定文字列を使用して、ループの各反復処理の結果を出力する例を次に示します。  
  
 [!code-cs[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 <xref:System.Console.WriteLine%2A> メソッドのオーバーロードは、パラメーターとして書式指定文字列を受け取ります。  したがって、メソッドを明示的に呼び出さずに書式指定リテラル文字列を埋め込むことができます。  ただし、<xref:System.Diagnostics.Trace.WriteLine%2A> メソッドを使用して Visual Studio の **\[出力\]** ウィンドウにデバッグ出力を表示する場合は、<xref:System.String.Format%2A> メソッドを明示的に呼び出す必要があります。これは、<xref:System.Diagnostics.Trace.WriteLine%2A> は、書式指定文字列ではなく文字列のみを受け入れるためです。  書式指定文字列の詳細については、「[型の書式設定](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)」を参照してください。  
  
## 部分文字列  
 部分文字列は、1 つの文字列に含まれる一連の文字です。  元の文字列の一部から新しい文字列を作成するには、<xref:System.String.Substring%2A> メソッドを使用します。  <xref:System.String.IndexOf%2A> メソッドを使用して、1 つまたは複数の部分文字列を検索できます。  指定されたすべての部分文字列を新しい文字列に置換するには、<xref:System.String.Replace%2A> メソッドを使用します。  <xref:System.String.Substring%2A> メソッドと同様に、<xref:System.String.Replace%2A> は実際には新しい文字列を返し、元の文字列は変更しません。  詳細については、「[方法 : String のメソッドを使用して文字列を検索する](../../../csharp/programming-guide/strings/how-to-search-strings-using-string-methods.md)」および「[方法 : 文字列の内容を変更する](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md)」を参照してください。  
  
 [!code-cs[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## 各文字へのアクセス  
 次の例に示すように、配列表記とインデックス値を使用すると、それぞれの文字への読み取り専用アクセスが可能になります。  
  
 [!code-cs[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 <xref:System.String> メソッドが、文字列内の個別の文字を変更する必要がある機能を提供していない場合は、<xref:System.Text.StringBuilder> オブジェクトを使用して個別の文字の "埋め込み先" を変更し、<xref:System.Text.StringBuilder> メソッドを使用することで、結果を格納する新しい文字列を作成できます。  次の例では、特定の方法で元の文字列を変更し、将来使用するためにその結果を保存する必要があるとします。  
  
 [!code-cs[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## null 文字列と空の文字列  
 空の文字列は、文字数ゼロの <xref:System.String?displayProperty=fullName> オブジェクトのインスタンスです。  空の文字列は、空のテキスト フィールドを表すため、さまざまなプログラミング シナリオでよく使用されます。  空の文字列は有効な <xref:System.String?displayProperty=fullName> オブジェクトなので、メソッドを呼び出すことができます。  空の文字列は、次のように初期化されます。  
  
```  
string s = String.Empty;  
```  
  
 一方、null 文字列は <xref:System.String?displayProperty=fullName> オブジェクトのインスタンスを参照しないので、null 文字列でメソッドを呼び出そうとすると <xref:System.NullReferenceException> が発生します。  しかし、null 文字列を他の文字列に連結したり、他の文字列と比較することは可能です。  次に、null 文字列の参照によって例外がスローされる場合とされない場合の例を示します。  
  
 [!code-cs[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## 文字列を迅速に作成するための StringBuilder の使用  
 .NET での文字列操作は高度に最適化されており、ほとんどの場合パフォーマンスに大きく影響することはありません。  ただし、短いループが数百回または数千回実行されている場合など、シナリオによっては文字列操作がパフォーマンスに影響する可能性があります。  <xref:System.Text.StringBuilder> クラスが作成する文字列バッファーにより、プログラムで大量の文字列操作を実行する場合のパフォーマンスが向上します。  <xref:System.Text.StringBuilder> 文字列を使用すると、組み込み文字列データ型ではサポートされていない個別の文字を再割り当てできます。  たとえば、このコードでは、新しい文字列を作成せずに、文字列の内容を変更します。  
  
 [!code-cs[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 この例では、<xref:System.Text.StringBuilder> オブジェクトを使用して、複数の数値型から 1 つの文字列を作成します。  
  
 [!code-cs[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## 文字列、拡張メソッド、および LINQ  
 <xref:System.String> 型は <xref:System.Collections.Generic.IEnumerable%601> を実装するため、<xref:System.Linq.Enumerable> クラスで定義されている拡張メソッドを文字列で使用できます。  見やすさを考慮して、これらのメソッドは <xref:System.String> 型の IntelliSense からは除外されていますが、使用できます。  文字列で [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] クエリ式を使用することもできます。  詳細については、「[LINQ and Strings](../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)」を参照してください。  
  
## 関連トピック  
  
|トピック|Description|  
|----------|-----------------|  
|[方法 : 文字列の内容を変更する](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md)|文字列の内容を変更するコード例を紹介します。|  
|[方法: 複数の文字列を連結する](../../../csharp/programming-guide/strings/how-to-concatenate-multiple-strings.md)|`+` 演算子と `Stringbuilder` クラスを使用して、コンパイル時および実行時に文字列を結合する方法について説明します。|  
|[方法 : 文字列を比較する](../../../csharp/programming-guide/strings/how-to-compare-strings.md)|文字列の序数比較を実行する方法を示します。|  
|[方法: String.Split を使用して文字列を解析する ](../../../csharp/programming-guide/strings/how-to-parse-strings-using-string-split.md)|`String.Split` メソッドを使用して文字列を解析するコード例を紹介します。|  
|[方法 : String のメソッドを使用して文字列を検索する](../../../csharp/programming-guide/strings/how-to-search-strings-using-string-methods.md)|特定のメソッドを使用して文字列を検索する方法について説明します。|  
|[方法 : 正規表現を使用して文字列を検索する](../../../csharp/programming-guide/strings/how-to-search-strings-using-regular-expressions.md)|正規表現を使用して文字列を検索する方法について説明します。|  
|[方法 : 文字列が数値を表しているかどうかを確認する](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|文字列を安全に解析して、有効な数値があるかどうかを確認する方法を示します。|  
|[方法 : 文字列を DateTime に変換する](../../../csharp/programming-guide/strings/how-to-convert-a-string-to-a-datetime.md)|"01\/24\/2008" などの文字列を <xref:System.DateTime?displayProperty=fullName> オブジェクトに変換する方法を示します。|  
|[基本的な文字列操作](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)|<xref:System.String?displayProperty=fullName> メソッドおよび <xref:System.Text.StringBuilder?displayProperty=fullName> メソッドを使用して基本的な文字列操作を実行するトピックへのリンクを示します。|  
|[文字列の解析](../Topic/Parsing%20Strings%20in%20the%20.NET%20Framework.md)|文字列に文字または空白を挿入する方法について説明します。|  
|[文字列の比較](../Topic/Comparing%20Strings%20in%20the%20.NET%20Framework.md)|文字列を比較する方法について説明し、C\# および Visual Basic での例を示します。|  
|[StringBuilder クラスの使用](../Topic/Using%20the%20StringBuilder%20Class%20in%20the%20.NET%20Framework.md)|<xref:System.Text.StringBuilder> クラスの動的な文字列オブジェクトを作成および変更する方法について説明します。|  
|[LINQ and Strings](../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)|LINQ クエリを使用してさまざまな文字列操作を実行する方法について説明します。|  
|[C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)|C\# のプログラミング要素について説明するトピックへのリンクを示します。|  
  
## 参考書籍の該当する章  
 [More About Variables](http://go.microsoft.com/fwlink/?LinkId=221230) 入力 [Beginning Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)