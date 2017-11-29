---
title: "#<a name=\"undef-c-reference\"></a>undef (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#undef'
helpviewer_keywords: '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a3c162c0ecb8bb39cc13a34dcd15fa3ce96ebb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="undef-c-reference"></a>#undef (C# リファレンス)
`#undef` を使用すると、シンボルを未定義にすることができます。未定義のシンボルを [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ディレクティブで式として使用すると、その式は `false` と評価されます。  
  
 シンボルは、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ディレクティブまたは [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) コンパイラ オプションで定義できます。 `#undef` ディレクティブは、ファイル内で、ディレクティブではない他のステートメントよりも前に記述する必要があります。  
  
## <a name="example"></a>例  
  
```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass   
{  
    static void Main()   
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```  
  
 **DEBUG が定義されていません**  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)
