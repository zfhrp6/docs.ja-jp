---
title: "アプリケーション開発での PNRP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 752b354df897fa37bc45c1bbd1969cf93aac87ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="pnrp-in-application-development"></a>アプリケーション開発での PNRP
Windows Vista では、ネットワーク アプリケーションは、簡単な PNRP アプリケーション プログラミング インターフェイス (API) を通して名前発行および名前解決機能にアクセスできます。  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>ピア名解決プロトコルの実装  
 簡略化された PNRP API では、名前とアドレスを登録するためにクラウドを明示的に指定することはありません。PNRP コンポーネントは、参加する適切なクラウドと、クラウド内で公開するアドレスを、自動的に決定ます。  
  
 Windows Vista の非常に簡略化された PNRP 名前解決では、Windows Sockets 関数 getaddrinfo() に PNRP 名が組み込まれています。 PNRP を使って名前を IPv6 アドレスに変換する場合、getaddrinfo() 関数を使って完全修飾ドメイン名 (FQDN) name.prnp.net を解決できます。ここで name は解決されるピア名です。 pnrp.net ドメインは、PNRP 名前解決のために Windows Vista で予約されているドメインです。  
  
 PeerToPeer アプリケーション間でのメッセージの受け渡しは、依然として PeerChannel や WCF の[大規模データとストリーミング](http://go.microsoft.com/fwlink/?LinkID=179652)などの、基盤のアーキテクチャによって処理されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.PeerToPeer>
