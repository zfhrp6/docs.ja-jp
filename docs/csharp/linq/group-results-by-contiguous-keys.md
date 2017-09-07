---
title: "連続するキーで結果をグループ化する"
description: "連続するキーで結果をグループ化する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ddd028a3aad5186ef6773b32e9f9e8e1cbff95fc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="group-results-by-contiguous-keys"></a>連続するキーで結果をグループ化する

要素をグループ化し、連続するキーのサブシーケンスを表すチャンクにする方法を次の例に示します。 たとえば、次の一連のキーと値のペアがあるとします。  
  
|キー|値|  
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
  
 [!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 プロジェクトで拡張メソッドを使用するには、`MyExtensions` 静的クラスを新規または既存のソース コード ファイルにコピーし、必要に応じて、配置されている名前空間の `using` ディレクティブを追加します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ クエリ式](index.md)   
 

