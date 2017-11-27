---
title: "CStr 関数の戻り値 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b498c9b1b7916467c96ed2c645c7131192a5e8b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>CStr 関数の戻り値 (Visual Basic)
次の表に、値を返します`CStr`の各データ型に対して`expression`です。  
  
|場合`expression`型|`CStr`返します。|  
|-----------------------------|--------------------|  
|[Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|"True"を含む文字列または"False"です。|  
|[Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)|含む文字列、`Date`システムの短い日付形式での値 (日付と時刻)。|  
|[数値のデータ型](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|数を表す文字列。|  
  
## <a name="cstr-and-date"></a>CStr と日付  
 `Date`型には常に日付と時刻の両方の情報が含まれています。 型変換のため、Visual Basic 1/1/0001 (1 年 1 月、1) であると見なす、*ニュートラル値*日付、および 00時 00分: 00 (午前 0 時) に依存しない値であることにします。 `CStr`結果の文字列に中立的な値は含まれません。 変換する場合など、`#January 1, 0001 9:30:00#`文字列に、結果は"9時 30分: 00 AM"以外の場合は、日付情報は表示されません。 ただし、日付情報は、元にまだ存在している`Date`値し、などの関数で回復できる<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>です。  
  
> [!NOTE]
>  `CStr`関数は、アプリケーションの現在のカルチャ設定に基づいて、変換を実行します。 特定のカルチャの数値の文字列形式を取得するには、数値を使用`ToString(IFormatProvider)`メソッドです。 たとえば、使用して<xref:System.Double.ToString%2A?displayProperty=nameWithType>型の値を変換するときに`Double`を`String`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)
