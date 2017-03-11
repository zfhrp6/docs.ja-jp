---
redirect_url: /dotnet/articles/csharp/linq/group-results-by-contiguous-keys
caps.handback.revision: 11
---
# 方法 : 連続するキーで結果をグループ化する (C# プログラミング ガイド)
要素を、連続するキーのサブシーケンスを表すチャンクにグループ化する方法を次の例に示します。  たとえば、次の一連のキーと値のペアがあるとします。  
  
|Key|値|  
|---------|-------|  
|A|We|  
|A|think|  
|A|that|  
|B|Linq|  
|C|is|  
|A|really|  
|B|cool|  
|B|\!|  
  
 次のグループがこの順序で作成されます。  
  
1.  We, think, that  
  
2.  Linq  
  
3.  is  
  
4.  really  
  
5.  cool, \!  
  
 ソリューションは、スレッド セーフであり、結果をストリーミングで返す拡張メソッドとして実装されます。  つまり、ソース シーケンス内を移動するときにグループが作成されます。  `group` 演算子または `orderby` 演算子とは異なり、すべてのシーケンスが読み取られる前に、呼び出し元にグループを返し始めることができます。  
  
 ソース コードのコメントで説明されているように、ソース シーケンスが反復処理されるときに各グループまたはチャンクのコピーを作成することで、スレッド セーフが実現されます。  ソース シーケンスに連続するアイテムの大きなシーケンスがある場合、共通言語ランタイムにより <xref:System.OutOfMemoryException> がスローされる可能性があります。  
  
## 使用例  
 拡張メソッドと、それを使用するクライアント コードを次の例に示します。  
  
 [!code-cs[cscsrefContiguousGroups#1](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/how-to-group-results-by-_1.cs)]  
  
 プロジェクトで拡張メソッドを使用するには、`MyExtensions` 静的クラスを新規または既存のソース コード ファイルにコピーし、必要に応じて、配置されている名前空間の `using` ディレクティブを追加します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Classification of Standard Query Operators by Manner of Execution](../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)