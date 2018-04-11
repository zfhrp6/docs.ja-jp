---
title: 名前空間 (C# プログラミング ガイド)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3eb645f5beb61d3cec97a70a54e660c65be52091
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-c-programming-guide"></a>名前空間 (C# プログラミング ガイド)
C# プログラミングでは、名前空間が 2 つの方法でよく使用されます。 最初の方法では、次のように .NET Framework で名前空間を使用して、その多くのクラスを整理します。  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` は名前空間で、`Console` はその名前空間内のクラスです。 以下の例のように、`using` キーワードを使用できるため、完全な名前は必要ありません。  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 詳細については、「[using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)」を参照してください。  
  
 2 つ目の方法では、独自の名前空間を宣言します。これは、より大きなプログラミング プロジェクトでクラス名とメソッド名のスコープを制御するのに役立ちます。 名前空間を宣言するには、以下の例のように、[namespace](../../../csharp/language-reference/keywords/namespace.md) キーワードを使用します。  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>名前空間の概要  
 名前空間には次の特徴があります。  
  
-   大きなコード プロジェクトを整理します。  
  
-   `.` 演算子を使用して、区切られます。  
  
-   `using directive` を使用すると、クラスごとに名前空間の名前を指定する必要がなくなります。  
  
-   `global` 名前空間は "ルート" 名前空間です。`global::System` は常に .NET Framework 名前空間の `System` を参照します。  
  
## <a name="related-sections"></a>関連項目  
 名前空間の詳細については、次のトピックを参照してください。  
  
-   [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [方法: グローバル名前空間エイリアスを使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [方法: My 名前空間を使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)  
 [:: 演算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [。演算子](../../../csharp/language-reference/operators/member-access-operator.md)
