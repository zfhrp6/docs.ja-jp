---
title: "&quot;&lt;classname&gt;&quot; ため CLS 準拠ではありません、インターフェイス &quot;&lt;interfacename&gt;&quot; その実装は CLS 準拠ではありません |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
dev_langs:
- VB
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
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
ms.openlocfilehash: 1e5c948ed5ddeaa2f8a8efd4aa83a2539cc862f3
ms.lasthandoff: 03/13/2017

---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a>'&lt;classname&gt;' ため CLS 準拠ではありません、インターフェイス '&lt;interfacename&gt;' その実装は CLS 準拠ではありません
クラスまたはインターフェイスが `<CLSCompliant(True)>` としてマークされていますが、これらの派生元の型、またはこれらが実装している型が `<CLSCompliant(False)>` としてマークされているか、マークされていません。  
  
 クラスまたはインターフェイスに対応して、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS) には、その全体の継承階層を対応にする必要があります。 つまり、直接的または間接的に継承する型をすべて CLS に準拠させる必要があります。 同様に、クラスが&1; つ以上のインターフェイスを実装する場合は、そのすべてのインターフェイスの継承階層全体を CLS 準拠にする必要があります。  
  
 適用すると、<xref:System.CLSCompliantAttribute>プログラミング要素に属性を設定する`isCompliant`するか、パラメーター`True`または`False`を対応または非対応を示します</xref:System.CLSCompliantAttribute>。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 適用しない場合、<xref:System.CLSCompliantAttribute>要素に準拠するいないと見なされます</xref:System.CLSCompliantAttribute>。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC40029  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   CLS 準拠にする必要がある場合は、この型を別の継承階層または実装スキームの中で定義します。  
  
-   この型が現在その継承階層または実装スキーム内に残ることが必要な場合は、削除、<xref:System.CLSCompliantAttribute>その定義からまたはとしてマークして`<CLSCompliant(False)>`</xref:System.CLSCompliantAttribute>。  
  
## <a name="see-also"></a>関連項目  
 [\<経由で PAVE > CLS 準拠のコードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
