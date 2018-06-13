---
title: XML データ型の変換
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c22ebed1127be6a32a09b428b977b1ba9ca0a7eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569367"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="bef07-102">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="bef07-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="bef07-103">**XmlConvert** クラスのメソッドのほとんどは、文字列と厳密に型指定された形式との間のデータ変換に使われます。</span><span class="sxs-lookup"><span data-stu-id="bef07-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="bef07-104">これらのメソッドはロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="bef07-104">Methods are locale independent.</span></span> <span data-ttu-id="bef07-105">つまり、変換の実行時にはロケールの設定は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="bef07-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="bef07-106">文字列を型として読み込む</span><span class="sxs-lookup"><span data-stu-id="bef07-106">Reading String as types</span></span>  
 <span data-ttu-id="bef07-107">文字列を読み込んで **DateTime** 型に変換するサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bef07-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="bef07-108">入力として次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="bef07-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="bef07-109">**入力**</span><span class="sxs-lookup"><span data-stu-id="bef07-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="bef07-110">次のコードは、文字列を **DateTime** 形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="bef07-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="bef07-111">文字列を型として書き込む</span><span class="sxs-lookup"><span data-stu-id="bef07-111">Writing Strings as types</span></span>  
 <span data-ttu-id="bef07-112">**Int32** を読み込んで文字列に変換するサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bef07-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="bef07-113">入力として次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="bef07-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="bef07-114">**入力**</span><span class="sxs-lookup"><span data-stu-id="bef07-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="bef07-115">次のコードは、**Int32** を **String** に変換します。</span><span class="sxs-lookup"><span data-stu-id="bef07-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="bef07-116">参照</span><span class="sxs-lookup"><span data-stu-id="bef07-116">See Also</span></span>  
 [<span data-ttu-id="bef07-117">文字列の .NET Framework データ型への変換</span><span class="sxs-lookup"><span data-stu-id="bef07-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="bef07-118">.NET Framework 型の文字列への変換</span><span class="sxs-lookup"><span data-stu-id="bef07-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
