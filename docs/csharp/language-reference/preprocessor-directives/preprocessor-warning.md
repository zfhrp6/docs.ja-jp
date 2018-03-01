---
title: "#warning (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8145c4a62d5179d6fa46e27186d83fc0108939d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="warning-c-reference"></a>#warning (C# リファレンス)
`#warning` を使用すると、コード内の特定の場所からレベル 1 の警告を生成できます。 例:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>コメント  
 `#warning` は条件付きディレクティブ内で一般的に使用されます。 [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md) を使用してユーザー定義のエラーを生成することもできます。  
  
## <a name="example"></a>例  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)
