---
title: "方法: FTP でディレクトリの内容を一覧表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 130c64c9-7b7f-4672-9b3b-d946bd2616c5
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f5f74b215fb753d8d5a12a3e203b8598fc258053
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-list-directory-contents-with-ftp"></a><span data-ttu-id="078f5-102">方法: FTP でディレクトリの内容を一覧表示する</span><span class="sxs-lookup"><span data-stu-id="078f5-102">How to: List Directory Contents with FTP</span></span>
<span data-ttu-id="078f5-103">このサンプルでは、FTP サーバーのディレクトリの内容を一覧表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="078f5-103">This sample shows how to list the directory contents of an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="078f5-104">例</span><span class="sxs-lookup"><span data-stu-id="078f5-104">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Get the object used to communicate with the server.  
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/");  
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Stream responseStream = response.GetResponseStream();  
            StreamReader reader = new StreamReader(responseStream);  
            Console.WriteLine(reader.ReadToEnd());  
  
            Console.WriteLine("Directory List Complete, status {0}", response.StatusDescription);  
  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="078f5-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="078f5-105">Compiling the Code</span></span>  
 <span data-ttu-id="078f5-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="078f5-106">This example requires:</span></span>  
  
-   <span data-ttu-id="078f5-107">**System.Net** 名前空間の参照。</span><span class="sxs-lookup"><span data-stu-id="078f5-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="078f5-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="078f5-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="078f5-109">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="078f5-109">.NET Framework Security</span></span>
