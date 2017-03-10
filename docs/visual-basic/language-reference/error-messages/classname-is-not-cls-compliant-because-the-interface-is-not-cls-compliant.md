---
title: "&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc40029"
  - "vbc40029"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40029"
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# &#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クラスまたはインターフェイスが `<CLSCompliant(True)>` でマーク付けされていますが、この継承元の型または実装している型が `<CLSCompliant(False)>` でマーク付けされているか、マークが付いていません。  
  
 クラスまたはインターフェイスを[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 準拠にするためには、継承階層全体を CLS に準拠させる必要があります。  つまり、直接的または間接的に継承するすべての型を CLS に準拠させる必要があります。  同様に、クラスが 1 つ以上のインターフェイスを実装する場合は、そのすべてのインターフェイスの継承階層全体を CLS 準拠にする必要があります。  
  
 <xref:System.CLSCompliantAttribute> をプログラミング要素に適用するときは、属性の `isCompliant` パラメーターを `True` または `False` に設定して準拠または非準拠を示します。  このパラメーターの既定値はありません。値を指定する必要があります。  
  
 <xref:System.CLSCompliantAttribute> を要素に適用しなかった場合は、非準拠と見なされます。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC40029  
  
### このエラーを解決するには  
  
-   CLS 準拠にする必要がある場合は、この型を別の継承階層または別の実装スキームに定義します。  
  
-   この型を現在の継承階層または実装スキームに残しておく必要がある場合は、<xref:System.CLSCompliantAttribute> を定義から削除するか、`<CLSCompliant(False)>` でマーク付けします。  
  
## 参照  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)