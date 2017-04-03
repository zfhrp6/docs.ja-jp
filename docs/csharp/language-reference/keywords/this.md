---
title: "this (C# リファレンス) | Microsoft Docs"
description: "this キーワード (C# リファレンス)"
keywords: "this (C#)、this キーワード (C#)、this キーワード (C# リファレンス)、this キーワード (C# 言語リファレンス)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
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
ms.openlocfilehash: 8e14a32f11b9661ae18fd718fb1a72385fa7f3a7
ms.lasthandoff: 03/13/2017

---
# <a name="this-c-reference"></a>this (C# リファレンス)
`this` キーワードはクラスの現在のインスタンスを参照します。拡張メソッドの最初のパラメーターの修飾子としても使用されます。  
  
> [!NOTE]
>  ここでは、クラス インスタンスでの `this` の使用について説明します。 拡張メソッドでの使用の詳細については、「[拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。  
  
 `this` の一般的な使い方を次に示します。  
  
-   似た名前によって非表示にされるメンバーを修飾する場合は次のようになります。  
  
 [!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   オブジェクトを他のメソッドにパラメーターとして渡す場合は次のようになります。  
  
    ```  
    CalcTax(this);  
    ```  
  
-   インデクサーを宣言する場合は、次のようになります。  
  
 [!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 静的メンバー関数は、クラス レベルで存在し、オブジェクトの一部ではないため、`this` ポインターがありません。 静的メソッドで `this` を参照するとエラーになります。  
  
## <a name="example"></a>例  
 この例では、似た名前によって非表示にされている `Employee` クラスのメンバー `name` と `alias` を修飾するために `this` が使用されています。 また、別のクラスに属するメソッド `CalcTax` にオブジェクトを渡すためにも使用されています。  
  
 [!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)
