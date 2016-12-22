---
title: "Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40033"
  - "vbc40033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40033"
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

インターフェイス内のプロパティ、プロシージャ、またはイベントが `<CLSCompliant(True)>` でマーク付けされていますが、そのインターフェイス自体が `<CLSCompliant(False)>` でマーク付けされているか、またはマークが付いていません。  
  
 インターフェイスが [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) に準拠している場合、そのすべてのメンバーも準拠している必要があります。  
  
 <xref:System.CLSCompliantAttribute> をプログラミング要素に適用するときは、属性の `isCompliant` パラメーターを `True` または `False` に設定して準拠または非準拠を示します。  このパラメーターの既定値はありません。値を指定する必要があります。  
  
 <xref:System.CLSCompliantAttribute> を要素に適用しなかった場合は、非準拠と見なされます。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC40033  
  
### このエラーを解決するには  
  
-   CLS 準拠にする必要があり、インターフェイスのソース コードを変更できる場合、かつすべてのメンバーが準拠している場合は、インターフェイスを `<CLSCompliant(True)>` でマーク付けします。  
  
-   CLS 準拠にする必要があり、インターフェイスのソース コードを変更できない場合、または CLS 準拠であるかどうかが明確でない場合は、このメンバーを別のインターフェイスに定義します。  
  
-   このメンバーを現在のインターフェイス内に残しておく必要がある場合は、インターフェイスの定義から <xref:System.CLSCompliantAttribute> を削除するか、`<CLSCompliant(False)>` でマーク付けします。  
  
## 参照  
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)