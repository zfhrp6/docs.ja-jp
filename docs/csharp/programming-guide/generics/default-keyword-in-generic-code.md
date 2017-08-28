---
title: "ジェネリック コードの default キーワード (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b5f5995b720d377717a5fff8a5e7e6e2196c612c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="default-keyword-in-generic-code-c-programming-guide"></a>ジェネリック コードの default キーワード (C# プログラミング ガイド)
ジェネリック クラスとジェネリック メソッドで発生する問題の 1 つは、次のことがあらかじめわかっていない場合に、パラメーター化された型 T に既定値を割り当てる方法です。  
  
-   T が参照型または値型のどちらか。  
  
-   T が値型の場合、T は数値か構造体か。  
  
 t をパラメーター化された型 T の変数であるとすると、ステートメント t = null は T が参照型の場合にのみ有効であり、t = 0 は数値型に対してのみ動作し、構造体の場合は動作しません。 このような場合の解決策は、`default` キーワードを使うことです。このキーワードは、参照型に対しては null を返し、値型に対しては 0 を返します。 構造体の場合は、構造体の各メンバーが値型か参照型かに応じて、0 または null に初期化されたメンバーを返します。 null 許容値型の場合は、default は構造体と同様に初期化される <xref:System.Nullable%601?displayProperty=fullName> を返します。  
  
 `GenericList<T>` クラスの次の例では、`default` キーワードを使う方法を示します。 詳しくは、「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」をご覧ください。  
  
 [!code-cs[csProgGuideGenerics#41](../../../csharp/programming-guide/generics/codesnippet/CSharp/default-keyword-in-generic-code_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../csharp/programming-guide/generics/index.md)   
 [ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)   
 [ジェネリック](~/docs/standard/generics/index.md)

