---
title: 連続するキーで結果をグループ化する
description: 連続するキーで結果をグループ化する方法。
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: a8d6ac133932a12154d5b23454065144c7652067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="group-results-by-contiguous-keys"></a>連続するキーで結果をグループ化する

要素をグループ化し、連続するキーのサブシーケンスを表すチャンクにする方法を次の例に示します。 たとえば、次の一連のキーと値のペアがあるとします。  
  
|キー|[値]|  
|---------|-----------|  
|A|水|  
|A|think|  
|A|that|  
|B|Linq|  
|C|is|  
|A|really|  
|B|cool|  
|B|!|  
  
 次のグループがこの順序で作成されます。  
  
1.  We, think, that  
  
2.  Linq  
  
3.  is  
  
4.  really  
  
5.  cool, !  
  
 ソリューションは、結果をストリーミングで返すスレッド セーフな拡張メソッドとして実装されます。 つまり、ソース シーケンス内を移動するときにグループが作成されます。 `group` 演算子や `orderby` 演算子とは異なり、すべてのシーケンスの読み取りが終わる前に、呼び出し元にグループを返し始めることができます。  
  
 ソース コードのコメントで説明されているように、ソース シーケンスが反復処理されるときに各グループまたはチャンクのコピーを作成することで、スレッド セーフが実現されます。 ソース シーケンスに連続するアイテムの大きなシーケンスがある場合、共通言語ランタイムにより <xref:System.OutOfMemoryException> がスローされる可能性があります。  
  
## <a name="example"></a>例  
 拡張メソッドと、それを使用するクライアント コードを次の例に示します。  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 プロジェクトで拡張メソッドを使用するには、`MyExtensions` 静的クラスを新規または既存のソース コード ファイルにコピーし、必要に応じて、配置されている名前空間の `using` ディレクティブを追加します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)  
 
