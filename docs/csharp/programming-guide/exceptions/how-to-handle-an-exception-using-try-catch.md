---
title: "方法: try-catch を使用して例外を処理する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9098bbcf5cefb85211f9d3bb9cac15943ba02172
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>方法: try/catch を使用して例外を処理する (C# プログラミング ガイド)
[try-catch](../../../csharp/language-reference/keywords/try-catch.md) ブロックの目的は、作業コードによって生成された例外をキャッチし、処理することです。 例外によっては、`catch` ブロックで処理し、例外を再スローせずに問題を解決できるものもありますが、多くの場合、適切な例外がスローされるようにする必要があります。  
  
## <a name="example"></a>例  
 この例の <xref:System.IndexOutOfRangeException> は最も適切な例外というわけではありません。呼び出し元から `index` 引数が渡されてエラーが発生しているため、より適切なメソッドは <xref:System.ArgumentOutOfRangeException> になります。  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>コメント  
 例外を発生させるコードは `try` ブロックに囲まれています。 `IndexOutOfRangeException` が発生した場合にこれを処理するための `catch` ステートメントが、すぐ後に追加されています。 `catch` ブロックは `IndexOutOfRangeException` を処理し、代わりにより適切な `ArgumentOutOfRangeException` 例外をスローします。 呼び出し元にできるだけ多くの情報を提供するため、元の例外を新しい例外の <xref:System.Exception.InnerException%2A> として指定することを検討してください。 <xref:System.Exception.InnerException%2A> プロパティは [readonly](../../../csharp/language-reference/keywords/readonly.md) であるため、新しい例外のコンストラクターで割り当てる必要があります。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [例外と例外処理](../../../csharp/programming-guide/exceptions/index.md)  
 [例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md)
