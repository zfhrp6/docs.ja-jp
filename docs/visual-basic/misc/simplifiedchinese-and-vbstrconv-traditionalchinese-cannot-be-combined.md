---
title: "SimplifiedChinese と VbStrConv.TraditionalChinese を組み合わせることはできません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArgument_StrConvSCandTC
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 57ab14cdcb3e4b27e821097dcfca4d97e1633035
ms.lasthandoff: 03/13/2017

---
# <a name="simplifiedchinese-and-vbstrconvtraditionalchinese-cannot-be-combined"></a>SimplifiedChinese と VbStrConv.TraditionalChinese を組み合わせることはできません。
アプリケーションが `VbStrConv` 列挙型メンバー `SimplifiedChinese` と `TraditionalChinese`を結合しようとしていますが、これらは相互に排他的です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   `VbStrConv.SimplifiedChinese` または `VbStrConv.TraditionalChinese`のいずれかを削除します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv 列挙型](http://msdn.microsoft.com/en-us/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [.NET Framework ベースの国際対応アプリケーションの概要](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
