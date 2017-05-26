---
title: "namespace (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namespace_CSharpKeyword
- namespace
dev_langs:
- CSharp
helpviewer_keywords:
- namespace keyword [C#]
- scope [C#]
ms.assetid: 0a788423-9110-42e0-97d9-bda41ca4870f
caps.latest.revision: 28
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
ms.openlocfilehash: cc90fe67f7c65d53980786c39f2a6f9869eec321
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="namespace-c-reference"></a>namespace (C# リファレンス)
`namespace` キーワードは、関連する一連のオブジェクトを含む範囲を宣言するために使用されます。 名前空間を利用し、コード要素を整理したり、グローバルに一意の型を作成したりできます。  
  
 [!code-cs[csrefKeywordsNamespace#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_1.cs)]  
  
## <a name="remarks"></a>コメント  
 名前空間内では、以下の型を 1 つ以上宣言できます。  
  
-   別の名前空間  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
-   [enum](../../../csharp/language-reference/keywords/enum.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
 C# ソース ファイル内に名前空間を明示的に宣言しているかどうかに関係なく、コンパイラは既定の名前空間を追加します。 この無名の名前空間はグローバル名前空間とも呼ばれますが、すべてのファイルに存在します。 グローバル名前空間内にある識別子は、名前付き名前空間で利用できます。  
  
 名前空間には暗黙的にパブリック アクセスが設定されます。この属性は変更できません。 名前空間内の要素に割り当てることができるアクセス修飾子については、「[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)」を参照してください。  
  
 名前空間は、2 つ以上の宣言で定義できます。 たとえば、次の例では、`MyCompany` 名前空間の一部として 2 つのクラスを定義しています。  
  
 [!code-cs[csrefKeywordsNamespace#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_2.cs)]  
  
## <a name="example"></a>例  
 入れ子になった名前空間で静的なメソッドを呼び出す方法の例を次に示します。  
  
 [!code-cs[csrefKeywordsNamespace#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/namespace_3.cs)]  
  
## <a name="for-more-information"></a>参照項目  
 名前空間の使用方法の詳細については、次のトピックを参照してください。  
  
-   [名前空間](../../../csharp/programming-guide/namespaces/index.md)  
  
-   [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [方法: グローバル名前空間エイリアスを使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [using](../../../csharp/language-reference/keywords/using.md)
