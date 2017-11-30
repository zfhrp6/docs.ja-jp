---
title: "XML データ型の変換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="7e872-102">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="7e872-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="7e872-103">メソッドの大部分がで見つかった、 **XmlConvert**文字列と厳密に型指定された形式間でデータを変換するクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e872-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="7e872-104">これらのメソッドはロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="7e872-104">Methods are locale independent.</span></span> <span data-ttu-id="7e872-105">つまり、変換の実行時にはロケールの設定は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="7e872-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="7e872-106">文字列を型として読み込む</span><span class="sxs-lookup"><span data-stu-id="7e872-106">Reading String as types</span></span>  
 <span data-ttu-id="7e872-107">次の例は、文字列を読み取り、に変換する、 **DateTime**型です。</span><span class="sxs-lookup"><span data-stu-id="7e872-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="7e872-108">入力として次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e872-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="7e872-109">**入力**</span><span class="sxs-lookup"><span data-stu-id="7e872-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="7e872-110">このコードを変換する文字列、 **DateTime**形式。</span><span class="sxs-lookup"><span data-stu-id="7e872-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="7e872-111">文字列を型として書き込む</span><span class="sxs-lookup"><span data-stu-id="7e872-111">Writing Strings as types</span></span>  
 <span data-ttu-id="7e872-112">次のサンプルの読み取り、 **Int32**文字列に変換します。</span><span class="sxs-lookup"><span data-stu-id="7e872-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="7e872-113">入力として次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e872-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="7e872-114">**入力**</span><span class="sxs-lookup"><span data-stu-id="7e872-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="7e872-115">このコードは、変換、 **Int32**に、**文字列**:</span><span class="sxs-lookup"><span data-stu-id="7e872-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e872-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e872-116">See Also</span></span>  
 [<span data-ttu-id="7e872-117">.NET Framework データ型を文字列に変換します。</span><span class="sxs-lookup"><span data-stu-id="7e872-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="7e872-118">.NET Framework の型を文字列に変換します。</span><span class="sxs-lookup"><span data-stu-id="7e872-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
