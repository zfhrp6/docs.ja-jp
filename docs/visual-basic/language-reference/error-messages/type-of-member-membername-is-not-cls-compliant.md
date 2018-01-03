---
title: "メンバー &#39; の種類&lt;membername&gt;&#39; CLS 準拠ではありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords: BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc82714d25efbe9d379fff36f92261cf25a78862
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a>メンバー &#39; の種類&lt;membername&gt;&#39; CLS 準拠ではありません
このメンバーに指定されたデータ型の一部、[言語非依存および言語非依存コンポーネント](../../../standard/language-independence-and-language-independent-components.md)(CLS)。 これは、エラーではありません、コンポーネント内であるため、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]と[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]このデータ型をサポートします。 ただし、厳密に CLS 準拠コードで記述された別のコンポーネントがこのデータ型をサポートしていません。 このようなコンポーネントはできないコンポーネントを正常にやり取りすることがあります。  
  
 次の [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] データ型は CLS に準拠していません。  
  
-   [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 既定では、このメッセージは警告です。 警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC40025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   場合は、コンポーネントが他のインターフェイス[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]コンポーネント、またはその他のコンポーネントとやり取りしない、何も変更する必要はありません。  
  
-   作成されていないコンポーネントとやり取りするかどうか、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リフレクションを判断できる場合があります、またはドキュメントを参照するかどうか、このデータ型がサポートされます。 その場合、何も変更する必要はありません。  
  
-   このデータ型をサポートしていないコンポーネントとやり取りする場合は、最も近い CLS 準拠型で置き換える必要があります。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
-   オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] とは異なることに注意してください。 たとえば、他の多くの環境では `uint` は 16 ビットです。 このようなコンポーネントに 16 ビットの引数を渡す場合として宣言`UShort`の代わりに`UInteger`、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コード。  
  
## <a name="see-also"></a>参照  
 [リフレクション](../../../framework/reflection-and-codedom/reflection.md)  
 
