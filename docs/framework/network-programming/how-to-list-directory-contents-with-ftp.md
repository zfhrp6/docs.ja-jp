---
title: '方法: FTP でディレクトリの内容を一覧表示する'
ms.date: 03/30/2017
ms.assetid: 130c64c9-7b7f-4672-9b3b-d946bd2616c5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 12351b06dc7d03971f9ce70f36110b8b6d672fd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394580"
---
# <a name="how-to-list-directory-contents-with-ftp"></a><span data-ttu-id="a2e81-102">方法: FTP でディレクトリの内容を一覧表示する</span><span class="sxs-lookup"><span data-stu-id="a2e81-102">How to: List Directory Contents with FTP</span></span>
<span data-ttu-id="a2e81-103">このサンプルでは、FTP サーバーのディレクトリの内容を一覧表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a2e81-103">This sample shows how to list the directory contents of an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2e81-104">例</span><span class="sxs-lookup"><span data-stu-id="a2e81-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2e81-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a2e81-105">Compiling the Code</span></span>  
 <span data-ttu-id="a2e81-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a2e81-106">This example requires:</span></span>  
  
-   <span data-ttu-id="a2e81-107">**System.Net** 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="a2e81-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a2e81-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="a2e81-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a2e81-109">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a2e81-109">.NET Framework Security</span></span>
