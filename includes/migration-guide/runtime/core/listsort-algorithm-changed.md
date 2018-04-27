### <a name="listsort-algorithm-changed"></a>List.Sort アルゴリズムが変更された

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、<xref:System.Collections.Generic.List%601?displayProperty=name> の並べ替えアルゴリズムが (クイック並べ替えではなく、内省的な並べ替えになるように) 変更されました。 <xref:System.Collections.Generic.List%601?displayProperty=name> の並べ替えは安定しますが、この変更により、さまざまなシナリオが不安定な方法で並べ替えられる可能性があります。 これは単に、同等の項目が API の後続の呼び出しで異なる順序で並べ替えられる可能性があることを意味します。|
|提案される解決策|以前の並べ替えアルゴリズムも不安定であるため (ただし、方法は若干異なる)、特定の順序で常に並べ替える同等の項目に依存するコードがあってはなりません。 それに依存していて、以前の動作で問題がないコードのインスタンスが存在する場合は、適切な順序で項目を決定論的に並べ替える比較子を使用するようにそのコードを更新する必要があります。|
|スコープ|透明|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|

