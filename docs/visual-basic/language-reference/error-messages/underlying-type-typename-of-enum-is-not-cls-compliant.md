---
title: "基になる型&lt;typename&gt;列挙型の CLS に準拠していません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords: BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68b57dc82737b72463b7fcf1a3e50934e1562c31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a>基になる型&lt;typename&gt;列挙型の CLS に準拠していません
この列挙体は、指定されたデータ型の一部、[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)(CLS)。 これは、エラーではありません、コンポーネント内であるため、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]と[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]このデータ型をサポートします。 ただし、厳密に CLS 準拠コードで記述された別のコンポーネントがこのデータ型をサポートしていません。 このようなコンポーネントはできないコンポーネントを正常にやり取りすることがあります。  
  
 次の [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] データ型は CLS に準拠していません。  
  
-   [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 既定では、このメッセージは警告です。 警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC40032  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   場合は、コンポーネントが他のインターフェイス[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]コンポーネント、またはその他のコンポーネントとやり取りしない、何も変更する必要はありません。  
  
-   作成されていないコンポーネントとやり取りするかどうか、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リフレクションを判断できる場合があります、またはドキュメントを参照するかどうか、このデータ型がサポートされます。 その場合、何も変更する必要はありません。  
  
-   このデータ型をサポートしていないコンポーネントとやり取りする場合は、最も近い CLS 準拠型で置き換える必要があります。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
-   オートメーション オブジェクトや COM オブジェクトとやり取りする場合は、一部の型のデータ幅が [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] とは異なることに注意してください。 たとえば、他の多くの環境では `uint` は 16 ビットです。 このようなコンポーネントに 16 ビットの引数を渡す場合として宣言`UShort`の代わりに`UInteger`、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コード。  
  
## <a name="see-also"></a>関連項目  
 [リフレクション](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)  
 [リフレクション](../../../framework/reflection-and-codedom/reflection.md)  
 [\<経由で PAVE > CLS 準拠コードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
