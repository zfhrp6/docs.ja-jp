---
title: "方法 : 文字列を DateTime に変換する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 15ef1ec4debf242cdabc42f26add890bd4b61507
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a><span data-ttu-id="2ba71-102">方法 : 文字列を DateTime に変換する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="2ba71-102">How to: Convert a String to a DateTime (C# Programming Guide)</span></span>
<span data-ttu-id="2ba71-103">プログラムでは、ユーザーが文字列値として日付を入力できるようにするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="2ba71-103">It is common for programs to enable users to enter dates as string values.</span></span> <span data-ttu-id="2ba71-104">文字列ベースの日付を <xref:System.DateTime?displayProperty=fullName> オブジェクトに変換するには、次の例に示すように、 <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> メソッドまたは <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> 静的メソッドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2ba71-104">To convert a string-based date to a <xref:System.DateTime?displayProperty=fullName> object, you can use the <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> method or the <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> static method, as shown in the following example.</span></span>  
  
 <span data-ttu-id="2ba71-105">**カルチャ**。</span><span class="sxs-lookup"><span data-stu-id="2ba71-105">**Culture**.</span></span>  <span data-ttu-id="2ba71-106">カルチャが異なると、日付文字列の記述方法も異なり場合があります。</span><span class="sxs-lookup"><span data-stu-id="2ba71-106">Different cultures in the world write date strings in different ways.</span></span>  <span data-ttu-id="2ba71-107">たとえば、米国では 2008 年 1 月 20 日を 01/20/2008 と記述します。</span><span class="sxs-lookup"><span data-stu-id="2ba71-107">For example, in the US 01/20/2008 is January 20th, 2008.</span></span>  <span data-ttu-id="2ba71-108">フランスでは、この値に対して InvalidFormatException がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2ba71-108">In France this will throw an InvalidFormatException.</span></span> <span data-ttu-id="2ba71-109">これは、フランスでは日付時刻を日/月/年として読み込み、米国では月/日/年として読み込むためです。</span><span class="sxs-lookup"><span data-stu-id="2ba71-109">This is because France reads date-times as Day/Month/Year, and in the US it is Month/Day/Year.</span></span>  
  
 <span data-ttu-id="2ba71-110">その結果、フランスでは 20/01/2008 の文字列は、2008 年 1 月 20 日と解釈されますが、米国では InvalidFormatException がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2ba71-110">Consequently, a string like 20/01/2008 will parse to January 20th, 2008 in France, and then throw an InvalidFormatException in the US.</span></span>  
  
 <span data-ttu-id="2ba71-111">現在のカルチャ設定を確認するには、System.Globalization.CultureInfo.CurrentCulture を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ba71-111">To determine your current culture settings, you can use System.Globalization.CultureInfo.CurrentCulture.</span></span>  
  
 <span data-ttu-id="2ba71-112">文字列を dateTime に変換する簡単な例については、次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ba71-112">See the example below for a simple example of converting a string to dateTime.</span></span>  
  
 <span data-ttu-id="2ba71-113">日付文字列の例については、「 <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ba71-113">For more examples of date strings, see <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>.</span></span>  
  
```csharp  
string dateTime = "01/08/2008 14:50:50.42";  
            DateTime dt = Convert.ToDateTime(dateTime);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond);  
            // Specify exactly how to interpret the string.  
            IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true);  
  
            // Alternate choice: If the string has been input by an end user, you might    
            // want to format it according to the current culture:   
            // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture;  
            DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond  
/* Output (assuming first culture is en-US and second is fr-FR):  
    Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Press any key to continue . . .  
 */  
```  
  
## <a name="example"></a><span data-ttu-id="2ba71-114">例</span><span class="sxs-lookup"><span data-stu-id="2ba71-114">Example</span></span>  
 <span data-ttu-id="2ba71-115">[!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ba71-115">[!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba71-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ba71-116">See Also</span></span>  
 [<span data-ttu-id="2ba71-117">文字列</span><span class="sxs-lookup"><span data-stu-id="2ba71-117">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

