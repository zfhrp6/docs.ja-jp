---
title: '&#39;です。&lt;interfacename&gt;.&lt;membername&gt;&#39; は、基本クラス &#39; によって既に実装されて&lt;baseclassname&gt;&#39;。 再実装&lt;型&gt;と見なされます'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69884ed567e0046da5cf5c51b3e83e57e890d49f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;です。&lt;interfacename&gt;.&lt;membername&gt;&#39; は、基本クラス &#39; によって既に実装されて&lt;baseclassname&gt;&#39;。 再実装&lt;型&gt;と見なされます
プロパティ、プロシージャ、または派生クラスでイベントを使用して、`Implements`句は、基底クラスで既に実装されているインターフェイス メンバーを指定します。  
  
 派生クラスでは、その基底クラスによって実装されているインターフェイス メンバーを再実装できます。 このことは、基底クラスの実装をオーバーライドすることとは異なります。 詳細については、次を参照してください。 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)です。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC42015  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   インターフェイス メンバーを再実装する場合は、操作を行う必要はありません。 派生クラス内のコードを使用する場合を除き、再実装されたメンバーにアクセスする、`MyBase`キーワードを基底クラスの実装にアクセスします。  
  
-   インターフェイス メンバーを再実装しない場合は、プロパティ、プロシージャ、またはイベント宣言から、 `Implements` 句を削除します。  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
