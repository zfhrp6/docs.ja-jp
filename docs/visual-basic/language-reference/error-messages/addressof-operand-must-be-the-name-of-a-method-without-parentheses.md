---
title: "& #39 です。AddressOf & #39;オペランドはかっこは不要メソッドの名前である必要があります。"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords: BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>& #39 です。AddressOf & #39;オペランドはかっこは不要メソッドの名前である必要があります。
`AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。 構文は次のとおりです。  
  
 `AddressOf``procedurename`  
  
 引数以下を囲むかっこを挿入した`AddressOf`[なし] が必要なします。  
  
 **エラー ID:** BC30577  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  引数以下、かっこを削除する`AddressOf`です。  
  
2.  引数がメソッド名を確認します。  
  
## <a name="see-also"></a>関連項目  
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
