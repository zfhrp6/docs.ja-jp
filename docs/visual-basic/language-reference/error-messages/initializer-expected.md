---
title: 初期化子が必要です
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46ff91ec240212571f7ec9f26e82d9d128263545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="initializer-expected"></a>初期化子が必要です
初期化リストが空で、次の例で示すように、オブジェクト初期化子を使用して、クラスのインスタンスを宣言しようとしました。  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 次の例で示すように、少なくとも 1 つのフィールドまたはプロパティは初期化子リストで初期化する必要があります。  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **エラー ID:** BC30996  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  少なくとも 1 つのフィールドまたはプロパティの初期化子で初期化またはオブジェクト初期化子を使用しないでください。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト初期化子 : 名前付きの型と匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [方法 : オブジェクト初期化子を使用してオブジェクトを宣言する](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
