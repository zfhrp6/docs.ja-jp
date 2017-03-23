---
title: "&quot;&lt;typename&gt;&quot; はデリゲート型です |。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
dev_langs:
- VB
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 3d6cc283f7e9815eb9b723a450731998f14b3424
ms.lasthandoff: 03/13/2017

---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>'&lt;typename&gt;' はデリゲート型です。
'\<typename >' はデリゲート型です。 デリゲートの構築では、引数リストとして単一の AddressOf 式のみを許可します。 多くの場合、デリゲートの構築ではなく、AddressOf 式を使用できます。  
  
 A`New`デリゲート クラスのインスタンスを作成する句は、デリゲート コンス トラクターに無効な引数リストを提供します。  
  
 1 つだけを指定する`AddressOf`新しいデリゲート インスタンスを作成するときの式。  
  
 失敗した場合、引数デリゲート コンス トラクターに複数の引数を渡すことも、1 つの引数を渡した場合、無効である場合にこのエラーが発生`AddressOf`式です。  
  
 **エラー ID:** BC32008  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   1 つを使用して`AddressOf`にデリゲート クラスの引数リスト内の式、`New`句。  
  
## <a name="see-also"></a>関連項目  
 [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)   
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [方法: デリゲート メソッドを呼び出す](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
