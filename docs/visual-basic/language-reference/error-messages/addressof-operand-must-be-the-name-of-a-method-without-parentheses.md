---
title: '&#39;AddressOf&#39;オペランドはかっこは不要メソッドの名前である必要があります'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583813"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39;AddressOf&#39;オペランドはかっこは不要メソッドの名前である必要があります
`AddressOf` 演算子は、特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。 構文は次のとおりです。  
  
 `AddressOf` `procedurename`  
  
 引数以下を囲むかっこを挿入した`AddressOf`[なし] が必要なします。  
  
 **エラー ID:** BC30577  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  引数以下、かっこを削除する`AddressOf`です。  
  
2.  引数がメソッド名を確認します。  
  
## <a name="see-also"></a>関連項目  
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
