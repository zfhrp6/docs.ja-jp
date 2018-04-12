---
title: この &#39; の最初のステートメント新しいサブ &#39;呼び出し &#39; にする必要があります。指定されて &#39;または &#39;です。'Mybase.new' &#39;(アクセス可能なコンス トラクターがないパラメーターなし)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1065643e1f6c868092fbad839af0dbbd33afaf01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a>この &#39; の最初のステートメント新しいサブ &#39;呼び出し &#39; にする必要があります。指定されて &#39;または &#39;です。'Mybase.new' &#39;(アクセス可能なコンス トラクターがないパラメーターなし)
この 'Sub New' の最初のステートメントが指定されて 'mybase.new' または 'myclass.new' への呼び出しをする必要があります基底クラス\<ベース名 >' の'\<derivedname >' は引数なしで呼び出せるアクセス可能な ' Sub New' がありません。  
  
 派生クラスでは、すべてのコンス トラクターが基底クラスのコンス トラクターを呼び出す必要があります (`MyBase.New`)。 基本クラスが派生クラスでアクセス可能なパラメーターなしのコンス トラクターを持つ場合`MyBase.New`自動的に呼び出すことができます。 いない場合は、パラメーターを持つ基本クラスのコンス トラクターを呼び出す必要があり、自動的にこのことはできません。 この場合、すべての派生クラスのコンス トラクターの最初のステートメントは、基本クラスでは、パラメーター化されたコンス トラクターを呼び出すか、呼び出す基底クラス コンス トラクターを派生クラスで別のコンス トラクターを呼び出す必要があります。  
  
 **エラー ID:** BC30148  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   呼び出すか`MyBase.New`必須のパラメーターを指定するか、このような呼び出しを行うピア コンス トラクターです。  
  
     たとえば、基本クラスとして宣言されたコンス トラクターがある場合`Public Sub New(ByVal index as Integer)`、最初のステートメントで、派生クラスのコンス トラクターがあります`MyBase.New(100)`です。  
  
## <a name="see-also"></a>関連項目  
 [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
