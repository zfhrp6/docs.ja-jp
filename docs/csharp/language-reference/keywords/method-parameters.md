---
title: メソッドのパラメーター (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 8a8d300661eec42030900dd9ee85a17e66aa0922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269347"
---
# <a name="method-parameters-c-reference"></a>メソッドのパラメーター (C# リファレンス)

[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) または [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) のないメソッドで宣言されたパラメーターは、呼び出されたメソッドに値で渡されます。 メソッドでその値を変更できますが、呼び出し元のプロシージャに制御が渡されるときに、変更された値は保持されません。 メソッド パラメーターのキーワードを使用して、この動作を変更できます。  
  
 ここでは、メソッドのパラメーターを宣言するときに使用できるキーワードについて説明します。  
  
-   [params](../../../csharp/language-reference/keywords/params.md) は、このパラメーターが異なる数の引数を取得する可能性があることを指定します。
  
-   [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) は、このパラメーターが参照によって渡されますが、呼び出されたメソッドでは読み取りのみが行われることを指定します。
  
-   [ref](../../../csharp/language-reference/keywords/ref.md) は、このパラメーターが参照によって渡され、呼び出されたメソッドでは読み取りまたは書き込みが行われる可能性があることを指定します。
  
-   [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) は、このパラメーターが参照によって渡され、呼び出されたメソッドでは書き込みが行われることを指定します。
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
