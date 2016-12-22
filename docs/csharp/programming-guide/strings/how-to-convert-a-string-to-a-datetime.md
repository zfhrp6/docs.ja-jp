---
title: "方法 : 文字列を DateTime に変換する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "文字列 [C#]、DateTime への変換"
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: 21
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : 文字列を DateTime に変換する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プログラムでは、ユーザーが文字列値として日付を入力できるようにするのが一般的です。 文字列ベースの日付を <xref:System.DateTime?displayProperty=fullName> オブジェクトに変換するには、次の例に示すように、<xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> メソッドまたは <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> 静的メソッドを使用することができます。  
  
 **カルチャ**。  カルチャが異なると、日付文字列の記述方法も異なり場合があります。  たとえば、米国では 2008 年 1 月 20 日を 01\/20\/2008 と記述します。  フランスでは、この値に対して InvalidFormatException がスローされます。 これは、フランスでは日付時刻を日\/月\/年として読み込み、米国では月\/日\/年として読み込むためです。  
  
 その結果、フランスでは 20\/01\/2008 の文字列は、2008 年 1 月 20 日と解釈されますが、米国では InvalidFormatException がスローされます。  
  
 現在のカルチャ設定を確認するには、System.Globalization.CultureInfo.CurrentCulture を使用します。  
  
 文字列を dateTime に変換する簡単な例については、次の例を参照してください。  
  
 日付文字列の例については、「<xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>」を参照してください。  
  
```vb  
string dateTime = "01/08/2008 14:50:50.42"; DateTime dt = Convert.ToDateTime(dateTime); Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}", dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond); // Specify exactly how to interpret the string. IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true); // Alternate choice: If the string has been input by an end user, you might // want to format it according to the current culture: // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture; DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal); Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}", dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond /* Output (assuming first culture is en-US and second is fr-FR): Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420 Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420 Press any key to continue . . . */  
```  
  
## 使用例  
 [!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]  
  
## 参照  
 [文字列](../../../csharp/programming-guide/strings/index.md)