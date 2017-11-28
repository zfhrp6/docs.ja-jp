---
title: "this (C# リファレンス)"
description: "this キーワード (C# リファレンス)"
keywords: "this (C#)、this キーワード (C#)、this キーワード (C# リファレンス)、this キーワード (C# 言語リファレンス)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords: this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a>this (C# リファレンス)
`this` キーワードはクラスの現在のインスタンスを参照します。拡張メソッドの最初のパラメーターの修飾子としても使用されます。  
  
> [!NOTE]
>  ここでは、クラス インスタンスでの `this` の使用について説明します。 拡張メソッドでの使用の詳細については、「[拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。  
  
 `this` の一般的な使い方を次に示します。  
  
-   似た名前によって非表示にされるメンバーを修飾する場合は次のようになります。  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   オブジェクトを他のメソッドにパラメーターとして渡す場合は次のようになります。  
  
    ```  
    CalcTax(this);  
    ```  
  
-   インデクサーを宣言する場合は、次のようになります。  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 静的メンバー関数は、クラス レベルで存在し、オブジェクトの一部ではないため、`this` ポインターがありません。 静的メソッドで `this` を参照するとエラーになります。  
  
## <a name="example"></a>例  
 この例では、似た名前によって非表示にされている `Employee` クラスのメンバー `name` と `alias` を修飾するために `this` が使用されています。 また、別のクラスに属するメソッド `CalcTax` にオブジェクトを渡すためにも使用されています。  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [base](../../../csharp/language-reference/keywords/base.md)  
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)
