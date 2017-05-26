---
title: "try-catch-finally (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
dev_langs:
- CSharp
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ebaf3d90c672bd3c069af12307f3745a12af3739
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="try-catch-finally-c-reference"></a>try-catch-finally (C# リファレンス)
通常、`catch` および `finally` は、`try` ブロックのリソースを取得して使用する場合に、対で記述されます。`catch` ブロックで例外的な状況を処理し、`finally` ブロックでリソースを解放します。  
  
 例外の再スローの使用例を含む詳細については、「[try-catch](../../../csharp/language-reference/keywords/try-catch.md)」および[例外のスロー](https://msdn.microsoft.com/library/xhcbs8fz)に関するページをご覧ください。 `finally` ブロックの詳細については、「[try-finally](../../../csharp/language-reference/keywords/try-finally.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-cs[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [try、throw、catch ステートメント (C++)](https://docs.microsoft.com/cpp/cpp/try-throw-and-catch-statements-cpp)   
 [例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [方法: 例外を明示的にスローする](https://msdn.microsoft.com/library/xhcbs8fz)   
 [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)
