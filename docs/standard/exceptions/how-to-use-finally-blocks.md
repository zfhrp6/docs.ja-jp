---
title: '方法 : finally ブロックを使用する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dff1083256e24a35b7238ee5e8af6cb5743bc0ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-finally-blocks"></a>finally ブロックを使用する方法

例外が発生すると、実行が停止され、コントロールが適切な例外ハンドラーに付与されます。 これは、多くの場合、実行されるはずのコード行がバイパスされることを意味します。 ファイルを閉じるなどのいくつかのリソースのクリーンアップは、例外がスローされた場合でも実行する必要があります。 これを行うために、`finally` ブロックを使用することができます。 `finally` ブロックは、例外がスローされるかどうかに関係なく、常に実行されます。

次のコード例では、`try`/`catch` ブロックを使用して <xref:System.ArgumentOutOfRangeException> をキャッチします。 `Main` メソッドは 2 つの配列を作成し、一方の配列をもう一方にコピーすることを試みます。 アクションが、<xref:System.ArgumentOutOfRangeException> を生成し、エラーは、コンソールに書き込まれます。 `finally` ブロックは、コピー操作の結果に関係なく実行されます。

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a>参照  
[例外](index.md)   
