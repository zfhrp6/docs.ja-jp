---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e491754b1c6c96e6afa9b172200cfb564307a8a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395075"
---
# <a name="ftp"></a><span data-ttu-id="cf251-102">FTP</span><span class="sxs-lookup"><span data-stu-id="cf251-102">FTP</span></span>
<span data-ttu-id="cf251-103">.NET Framework は、<xref:System.Net.FtpWebRequest> クラスと <xref:System.Net.FtpWebResponse> クラスを使用して、FTP プロトコルの包括的なサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="cf251-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="cf251-104">これらのクラスは <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> から派生します。</span><span class="sxs-lookup"><span data-stu-id="cf251-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="cf251-105">ほとんどの場合、<xref:System.Net.WebRequest> クラスと <xref:System.Net.WebResponse> クラスは、要求を行うために必要なすべてを提供しますが、プロパティとして公開されている FTP 固有の機能にアクセスする必要がある場合は、これらのクラスを <xref:System.Net.FtpWebRequest> または <xref:System.Net.FtpWebResponse> に型キャストすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf251-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="cf251-106">使用例</span><span class="sxs-lookup"><span data-stu-id="cf251-106">Examples</span></span>  
 <span data-ttu-id="cf251-107">詳細については、「[How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md)」(方法: FTP を使用してファイルをダウンロードする)、「[How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md)」(方法: FTP を使用してファイルをアップロードする)、および「[How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md)」(方法: FTP でディレクトリの内容を一覧表示する) のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf251-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="cf251-108">FTP とプロキシ</span><span class="sxs-lookup"><span data-stu-id="cf251-108">FTP and proxies</span></span>  
 <span data-ttu-id="cf251-109">(<xref:System.Net.FtpWebRequest.Proxy%2A> プロパティで指定された) プロキシが HTTP プロキシの場合、<xref:System.Net.WebRequestMethods.Ftp.DownloadFile>、<xref:System.Net.WebRequestMethods.Ftp.ListDirectory>、および <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> コマンドのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="cf251-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf251-110">参照</span><span class="sxs-lookup"><span data-stu-id="cf251-110">See Also</span></span>  
 [<span data-ttu-id="cf251-111">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="cf251-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="cf251-112">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="cf251-112">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="cf251-113">FTP クライアント テクノロジのサンプル</span><span class="sxs-lookup"><span data-stu-id="cf251-113">FTP Client Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [<span data-ttu-id="cf251-114">FTP エクスプローラー テクノロジのサンプル</span><span class="sxs-lookup"><span data-stu-id="cf251-114">FTP Explorer Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [<span data-ttu-id="cf251-115">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="cf251-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
