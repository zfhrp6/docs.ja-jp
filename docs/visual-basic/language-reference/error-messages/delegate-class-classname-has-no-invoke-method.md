---
title: "デリゲート クラス&lt;classname&gt;&quot; この型の式がメソッド呼び出しの対象にすることはできませんので Invoke メソッドを持たない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
dev_langs:
- VB
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ddc5ef0f0b3e9baa58f17dafb727e250c0fba9fd
ms.lasthandoff: 03/13/2017

---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>デリゲート クラス&lt;classname&gt;' れていない Invoke メソッドのため、この型の式がメソッド呼び出しの対象にすることはできません
呼び出し`Invoke`がデリゲートからが失敗したため`Invoke`デリゲート クラスで実装されていません。  
  
 **エラー ID:** BC30220  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  デリゲート クラスのインスタンスが作成されたことを確認、`Dim`ステートメントと、プロシージャがデリゲートのインスタンスに割り当てられたこと、`AddressOf`演算子。  
  
2.  デリゲート クラスを実装するコードを見つけてを実装しているかどうかを確認、`Invoke`プロシージャです。  
  
## <a name="see-also"></a>関連項目  
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)
