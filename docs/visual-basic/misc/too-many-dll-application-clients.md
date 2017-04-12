---
title: "DLL アプリケーションのクライアントが多すぎる |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
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
ms.openlocfilehash: 1abc9ce574de00db42a33cde478ca80be74e61ff
ms.lasthandoff: 03/13/2017

---
# <a name="too-many-dll-application-clients"></a>DLL のクライアント アプリケーションの数が多すぎます
ダイナミック リンク ライブラリ (DLL)[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]限られた数のホスト アプリケーションでのアクセスにのみ対応できます。 アプリケーションとその他のアプリケーションである[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)](アプリケーションでのアクセス可能性があります) のホストがすべてにアクセスしようとして、[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]同時 DLL です。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   開いているアプリケーションへのアクセスの数を減らす[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
## <a name="see-also"></a>関連項目  
 [エラーの種類](../../visual-basic/programming-guide/language-features/error-types.md)
