---
title: "&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;. Re-implementation of &lt;type&gt; assumed | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42015"
  - "bc42015"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42015"
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# &#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;. Re-implementation of &lt;type&gt; assumed
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

派生クラスのプロパティ、プロシージャ、またはイベントに、インターフェイス メンバーを指定する `Implements` 句が使用されていますが、そのメンバーは基本クラスで既に実装されています。  
  
 基本クラスで実装されたインターフェイス メンバーを、派生クラスで再実装することは可能です。  これは、基本クラスの実装をオーバーライドするということではありません。  詳細については、「[Implements](../../../visual-basic/language-reference/statements/implements-clause.md)」を参照してください。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC42015  
  
### このエラーを解決するには  
  
-   インターフェイス メンバーを再実装する場合は、特別なアクションは必要ありません。  `MyBase` キーワードを使って基本クラスの実装にアクセスしない限り、派生クラスのコードでは再実装したメンバーがアクセスされます。  
  
-   インターフェイス メンバーを再実装しない場合は、`Implements` 句をプロパティ、プロシージャ、またはイベントの宣言から削除します。  
  
## 参照  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)