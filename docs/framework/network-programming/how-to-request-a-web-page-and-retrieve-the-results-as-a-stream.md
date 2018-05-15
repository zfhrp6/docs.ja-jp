---
title: '方法: Web ページを要求し、ストリームとして結果を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 31856e7fc7136b3bdb8fab9fdf8185de32a3007a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="7705b-102">方法: Web ページを要求し、ストリームとして結果を取得する</span><span class="sxs-lookup"><span data-stu-id="7705b-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="7705b-103">この例では、Web ページを要求し、ストリームとして結果を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7705b-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7705b-104">例</span><span class="sxs-lookup"><span data-stu-id="7705b-104">Example</span></span>  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7705b-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="7705b-105">Compiling the Code</span></span>  
 <span data-ttu-id="7705b-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7705b-106">This example requires:</span></span>  
  
-   <span data-ttu-id="7705b-107"><xref:System.IO> 名前空間と <xref:System.Net> 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="7705b-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7705b-108">参照</span><span class="sxs-lookup"><span data-stu-id="7705b-108">See Also</span></span>  
 [<span data-ttu-id="7705b-109">データの要求</span><span class="sxs-lookup"><span data-stu-id="7705b-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
