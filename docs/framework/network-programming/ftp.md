---
title: FTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 6c0e0172bc42b0b14eebdeaba85d454c5aec25c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ftp"></a>FTP
.NET Framework は、<xref:System.Net.FtpWebRequest> クラスと <xref:System.Net.FtpWebResponse> クラスを使用して、FTP プロトコルの包括的なサポートを提供します。 これらのクラスは <xref:System.Net.WebRequest> と <xref:System.Net.WebResponse> から派生します。 ほとんどの場合、<xref:System.Net.WebRequest> クラスと <xref:System.Net.WebResponse> クラスは、要求を行うために必要なすべてを提供しますが、プロパティとして公開されている FTP 固有の機能にアクセスする必要がある場合は、これらのクラスを <xref:System.Net.FtpWebRequest> または <xref:System.Net.FtpWebResponse> に型キャストすることができます。  
  
## <a name="examples"></a>使用例  
 詳細については、「[How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md)」(方法: FTP を使用してファイルをダウンロードする)、「[How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md)」(方法: FTP を使用してファイルをアップロードする)、および「[How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md)」(方法: FTP でディレクトリの内容を一覧表示する) のトピックを参照してください。  
  
## <a name="ftp-and-proxies"></a>FTP とプロキシ  
 (<xref:System.Net.FtpWebRequest.Proxy%2A> プロパティで指定された) プロキシが HTTP プロキシの場合、<xref:System.Net.WebRequestMethods.Ftp.DownloadFile>、<xref:System.Net.WebRequestMethods.Ftp.ListDirectory>、および <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> コマンドのみがサポートされます。  
  
## <a name="see-also"></a>参照  
 [プロキシを介したインターネットへのアクセス](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)  
 [FTP クライアント テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179557)  
 [FTP エクスプローラー テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179569)  
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)
