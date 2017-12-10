---
title: "&#39;です。&lt;classname&gt;&#39; ためには CLS 準拠インターフェイス &#39;&lt;interfacename&gt;&#39;、implements は CLS 準拠ではありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
helpviewer_keywords: BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60c41332d3a5d93b05df906eefdeeb0d1b67e638
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>&#39;です。&lt;classname&gt;&#39; ためには CLS 準拠インターフェイス &#39;&lt;interfacename&gt;&#39;、implements は CLS 準拠ではありません
クラスまたはインターフェイスが `<CLSCompliant(True)>` としてマークされていますが、これらの派生元の型、またはこれらが実装している型が `<CLSCompliant(False)>` としてマークされているか、マークされていません。  
  
 クラスまたはインターフェイスに準拠する、[言語非依存および言語非依存コンポーネント](../../../../docs/standard/language-independence-and-language-independent-components.md)(CLS) に、継承階層全体は準拠である必要があります。 つまり、直接的または間接的に継承する型をすべて CLS に準拠させる必要があります。 同様に、クラスが 1 つ以上のインターフェイスを実装する場合は、そのすべてのインターフェイスの継承階層全体を CLS 準拠にする必要があります。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40029  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   CLS 準拠にする必要がある場合は、この型を別の継承階層または実装スキームの中で定義します。  
  
-   この型を現在の継承階層または実装スキームに残しておく必要がある場合は、 <xref:System.CLSCompliantAttribute> を定義から削除するか、 `<CLSCompliant(False)>`としてマークします。  
  
## <a name="see-also"></a>関連項目  
 [\<経由で PAVE > CLS 準拠コードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
