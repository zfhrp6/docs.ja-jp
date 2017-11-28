---
title: "インターネット要求の作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 52f1fc2601aca9b4d823d42ed961fcf007e5e5ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="creating-internet-requests"></a>インターネット要求の作成
アプリケーションは、<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> メソッドを使用して <xref:System.Net.WebRequest> のインスタンスを作成します。 これは、渡された URI スキームに基づいて **WebRequest** から派生するクラスを作成する静的メソッドです。  
  
## <a name="web-file-and-ftp-requests"></a>Web、ファイルおよび FTP 要求  
 .NET Framework は、**WebRequest** から派生する <xref:System.Net.HttpWebRequest> クラスを提供することにより、HTTP および HTTPS 要求を処理します。 ほとんどの場合、**WebRequest** クラスは要求を行うのに必要なすべてのプロパティを提供しますが、必要に応じて、**WebRequest.Create** メソッドで作成した **WebRequest** オブジェクトを **HttpWebRequest** 型にキャストすることにより、その要求の HTTP 固有のプロパティにアクセスすることができます。 同様に、**HttpWebResponse** オブジェクトは、HTTP および HTTPS 要求からの応答を処理します。 **HttpWebResponse** オブジェクトの HTTP 固有のプロパティにアクセスするには、**WebResponse** オブジェクトを **HttpWebResponse** 型にキャストする必要があります。  
  
 .NET Framework では、URI スキームの "file:" を使用するリソースの要求を処理するために、<xref:System.Net.FileWebRequest> および <xref:System.Net.FileWebResponse> クラスも提供します。 同様に、"ftp:" スキームを使用するリソースの要求を処理するために、<xref:System.Net.FtpWebRequest> および <xref:System.Net.FtpWebResponse> クラスが提供されます。 要求が、これらのスキームのいずれかを使用するリソースに対するものである場合、**WebRequest.Create** メソッドを使用して、要求を行うために使用するオブジェクトを取得できます。  
  
 アプリケーション レベルの他のプロトコルを使用する要求を処理するには、**WebRequest** および **WebResponse** から派生するプロトコル固有のクラスを実装する必要があります。 詳細については、「[Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md)」(プラグ可能なプロトコルのプログラミング) を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: WebRequest クラスを使用してデータを要求する](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [データの要求](../../../docs/framework/network-programming/requesting-data.md)
