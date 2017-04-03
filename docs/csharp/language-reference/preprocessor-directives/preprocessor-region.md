---
title: "#region (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
dev_langs:
- CSharp
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2924daffcdc44c8f5ba5cf97c5b141c0dd07ca4a
ms.lasthandoff: 03/13/2017

---
# <a name="region-c-reference"></a>#region (C# リファレンス)
`#region` を使用すると、コード ブロックを指定できます。このブロックは、Visual Studio コード エディターの[アウトライン](https://docs.microsoft.com/visualstudio/ide/outlining)機能を使用して展開や折りたたみを行うことができます。 コード ファイルが長い場合は、現在操作している部分に集中できるように 1 つ以上の領域を折りたたむ (非表示にする) ことができると便利です。 次の例では、領域を定義する方法を示します。  
  
```  
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>コメント  
 `#region` ブロックは、[#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) ディレクティブで終了させる必要があります。  
  
 `#region` ブロックは、[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ブロックと重複することはできません。 ただし、`#region` ブロックを `#if` ブロック内に入れ子にしたり、`#if` ブロックを `#region` ブロック内に入れ子にしたりすることはできます。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)

