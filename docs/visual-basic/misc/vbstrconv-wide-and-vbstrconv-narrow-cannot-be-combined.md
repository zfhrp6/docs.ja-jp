---
title: "VbStrConv.Wide と VbStrConv.Narrow を組み合わせることはできません。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 8d184fab3a63bc69caa67f315a9cb0f32514e2c1
ms.lasthandoff: 03/13/2017

---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a>VbStrConv.Wide と VbStrConv.Narrow を組み合わせることはできません
アプリケーションが `VbStrConv` 列挙型メンバー `Wide` と `Narrow`を結合しようとしていますが、これらは相互に排他的です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  `VbStrConv.Wide` または `VbStrConv.Narrow`のいずれかを削除します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv 列挙型](http://msdn.microsoft.com/en-us/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [.NET Framework ベースの国際対応アプリケーションの概要](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
