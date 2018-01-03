---
title: "非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords: BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74744b89ad72b6fd051f83ba38354d0a277555c8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>非 CLS 準拠&lt;membername&gt; CLS 準拠インターフェイスでは許可されません
プロパティ、プロシージャ、またはインターフェイスでイベントとしてマークされている`<CLSCompliant(True)>`インターフェイス自体としてマークされている場合`<CLSCompliant(False)>`またはマークされていません。  
  
 インターフェイスに準拠する、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS) に、そのすべてのメンバーは、準拠である必要があります。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定して、準拠または非準拠を示します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40033  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   CLS 準拠が必要 インターフェイスのソース コードを制御して、マークとしてインターフェイス`<CLSCompliant(True)>`すべてのメンバーに対応している場合。  
  
-   CLS 準拠する必要があり、インターフェイスのソース コードに制御がない場合、または準拠しているが満たしていない場合は、このメンバーを別のインターフェイスを定義します。  
  
-   このメンバーが、現在インターフェイス内に残ることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>をその定義からとしてマークまたは`<CLSCompliant(False)>`です。  
  
## <a name="see-also"></a>参照  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 
