---
title: "型&lt;typename&gt; CLS 準拠ではありません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d45da3b061dff0f82c1155daf5724033261bbdaa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>型&lt;typename&gt; CLS 準拠ではありません
変数、プロパティ、または関数の戻り値は、CLS 準拠ではないデータ型で宣言します。  
  
 準拠するアプリケーションの[言語非依存および言語非依存コンポーネント](https://msdn.microsoft.com/library/12a7a7h3)CLS 準拠型のみを使用して必要があります (CLS) にします。  
  
 次の [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] データ型は CLS に準拠していません。  
  
-   [SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **エラー ID:** BC40041  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   場合は、アプリケーションは、CLS に準拠する必要がある、この要素のデータ型を最も近い CLS 準拠型に変更します。 たとえば、2,147,483,647 を超える値の範囲が不要な場合は、 `UInteger` の代わりに `Integer` を使用できます。 拡張範囲が必要な場合は、 `UInteger` の代わりに `Long`を使用できます。  
  
-   アプリケーションが CLS に準拠させる必要がない場合は、何も変更する必要はありません。 注意してください、コンプライアンス非対応のただしです。  
  
## <a name="see-also"></a>関連項目  
 [\<経由で PAVE > CLS 準拠コードの記述](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
