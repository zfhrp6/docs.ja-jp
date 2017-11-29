---
title: "方法 : 文字列を DateTime に変換する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b459f245f0090fff16918bceb12a0082f6944331
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a><span data-ttu-id="5c3e8-102">方法 : 文字列を DateTime に変換する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5c3e8-102">How to: Convert a String to a DateTime (C# Programming Guide)</span></span>
<span data-ttu-id="5c3e8-103">プログラムでは、ユーザーが文字列値として日付を入力できるようにするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-103">It is common for programs to enable users to enter dates as string values.</span></span> <span data-ttu-id="5c3e8-104">文字列ベースの日付を <xref:System.DateTime?displayProperty=nameWithType> オブジェクトに変換するには、次の例に示すように、 <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType> メソッドまたは <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> 静的メソッドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-104">To convert a string-based date to a <xref:System.DateTime?displayProperty=nameWithType> object, you can use the <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType> method or the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> static method, as shown in the following example.</span></span>  
  
 <span data-ttu-id="5c3e8-105">**カルチャ**。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-105">**Culture**.</span></span>  <span data-ttu-id="5c3e8-106">カルチャが異なると、日付文字列の記述方法も異なり場合があります。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-106">Different cultures in the world write date strings in different ways.</span></span>  <span data-ttu-id="5c3e8-107">たとえば、米国では 2008 年 1 月 20 日を 01/20/2008 と記述します。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-107">For example, in the US 01/20/2008 is January 20th, 2008.</span></span>  <span data-ttu-id="5c3e8-108">フランスでは、この値に対して InvalidFormatException がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-108">In France this will throw an InvalidFormatException.</span></span> <span data-ttu-id="5c3e8-109">これは、フランスでは日付時刻を日/月/年として読み込み、米国では月/日/年として読み込むためです。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-109">This is because France reads date-times as Day/Month/Year, and in the US it is Month/Day/Year.</span></span>  
  
 <span data-ttu-id="5c3e8-110">その結果、フランスでは 20/01/2008 の文字列は、2008 年 1 月 20 日と解釈されますが、米国では InvalidFormatException がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-110">Consequently, a string like 20/01/2008 will parse to January 20th, 2008 in France, and then throw an InvalidFormatException in the US.</span></span>  
  
 <span data-ttu-id="5c3e8-111">現在のカルチャ設定を確認するには、System.Globalization.CultureInfo.CurrentCulture を使用します。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-111">To determine your current culture settings, you can use System.Globalization.CultureInfo.CurrentCulture.</span></span>  
  
 <span data-ttu-id="5c3e8-112">文字列を dateTime に変換する簡単な例については、次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-112">See the example below for a simple example of converting a string to dateTime.</span></span>  
  
 <span data-ttu-id="5c3e8-113">日付文字列の例については、「 <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c3e8-113">For more examples of date strings, see <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=nameWithType>.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5c3e8-114">例</span><span class="sxs-lookup"><span data-stu-id="5c3e8-114">Example</span></span>  
 [!code-csharp[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5c3e8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c3e8-115">See Also</span></span>  
 [<span data-ttu-id="5c3e8-116">文字列</span><span class="sxs-lookup"><span data-stu-id="5c3e8-116">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
