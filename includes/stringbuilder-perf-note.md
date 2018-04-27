<xref:System.Text.StringBuilder.Chars%2A> プロパティで文字ベースのインデックス付けを使用すると、次の条件下では非常に遅くなることがあります。

- <xref:System.Text.StringBuilder> インスタンスが大きい (たとえば、数万文字が含まれている)。
- <xref:System.Text.StringBuilder> が "チャンク化" している。 つまり、<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> などのメソッドの反復的な呼び出しにより、オブジェクトの <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> プロパティが自動的に展開され、メモリの新しいチャンクがそれに割り当てられています。

文字にアクセスするたびに、チャンクのリンク リスト全体が走査されて、インデックスを付ける適切なバッファーが検索されるため、パフォーマンスが著しく低下します。

> [!NOTE]
>  大きな "チャンク化" した <xref:System.Text.StringBuilder> オブジェクトの場合でも、1 つまたは少数の文字へのインデックス ベースのアクセスに <xref:System.Text.StringBuilder.Chars%2A> プロパティを使うと、パフォーマンスへの影響はごくわずかです。通常、これは **0(n)** 操作です。 <xref:System.Text.StringBuilder> オブジェクト内の文字を反復処理するときは、パフォーマンスに大きな影響が発生します。これは、**O(n^2)** 操作でます。 

<xref:System.Text.StringBuilder> オブジェクトで文字ベースのインデックス付けを使うときにパフォーマンスの問題が発生する場合は、次のいずれかの回避策を使うことができます。

- <xref:System.Text.StringBuilder.ToString%2A> メソッドを呼び出して <xref:System.Text.StringBuilder> インスタンスを <xref:System.String> に変換した後、文字列内の文字にアクセスします。

- 既存の <xref:System.Text.StringBuilder> オブジェクトの内容を、事前にサイズを設定した新しい <xref:System.Text.StringBuilder> オブジェクトにコピーします。 新しい <xref:System.Text.StringBuilder> オブジェクトはチャンク化していないため、パフォーマンスが向上します。 例:

   ```csharp
   // sbOriginal is the existing StringBuilder object
   var sbNew = new StringBuilder(sbOriginal.ToString(), sbOriginal.Length);
   ```
   ```vb
   ' sbOriginal is the existing StringBuilder object
   Dim sbNew = New StringBuilder(sbOriginal.ToString(), sbOriginal.Length)
   ```
- <xref:System.Text.StringBuilder.%23ctor(System.Int32)> コンストラクターを呼び出して、<xref:System.Text.StringBuilder> オブジェクトの初期容量を、予想される最大サイズにほぼ等しい値に設定します。 このようにすると、<xref:System.Text.StringBuilder> が最大容量に達することがほとんどない場合であっても、メモリ ブロック全体が割り当てられることに注意してください。
