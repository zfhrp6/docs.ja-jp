---
title: "方法 : 正規表現を使用して文字列を検索する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a>方法 : 正規表現を使用して文字列を検索する (C# プログラミング ガイド)
文字列の検索には、<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> クラスを使用できます。 単純な検索から、正規表現を活用した複雑な検索まで、さまざまな検索があります。 <xref:System.Text.RegularExpressions.Regex> クラスを使用して文字列を検索する 2 つの例を次に示します。 詳細については、「[.NET Framework の正規表現](https://msdn.microsoft.com/library/hs600312)」を参照してください。  
  
## <a name="example"></a>例  
 次のコードは、大文字と小文字を区別せずに配列の文字列を単純に検索するコンソール アプリケーションです。 静的メソッド <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> では、検索する文字列と、検索パターンを含む文字列を前提として、検索を実行します。 この場合、3 つ目の引数を使用して、大文字と小文字の区別を無視することを示します。 詳細については、「<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>」を参照してください。  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a>例  
 次のコードは、正規表現を使用して、配列の各文字列の形式を検証するコンソール アプリケーションです。 各文字列が電話番号の形式であることが検証されます。つまり、3 グループの数値がダッシュで区切られ、最初の 2 グループには 3 桁の数値が含まれ、3 つ目のグループには 4 桁の数値が含まれることが検証されます。 この操作は、正規表現 `^\\d{3}-\\d{3}-\\d{4}$` を使用して実行されます。 詳細については、「[正規表現言語 - クイック リファレンス](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)」をご覧ください。  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [文字列](../../../csharp/programming-guide/strings/index.md)  
 [.NET Framework 正規表現](https://msdn.microsoft.com/library/hs600312)  
 [正規表現言語 - クイック リファレンス](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
