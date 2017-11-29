---
title: ".NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 65d80734bfbe16c8b5052f8de1e4c6280b663707
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス
アンマネージ インターフェイスについて説明ホストを使用して、共通言語ランタイム (CLR) 統合、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、以降のバージョンのアプリケーションにします。 これらのインターフェイスは、ホストを構成して、ランタイムをプロセスに読み込むのためのメソッドを提供します。  
  
 以降で、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]、すべてのホスト インターフェイスで次の特性があります。  
  
-   有効期間の管理を使用する (`AddRef`と`Release`)、(暗黙的なコンテキストなど) をカプセル化し、 `QueryInterface` COM から  
  
-   ある型を使用しない COM など`BSTR`、 `SAFEARRAY`、または`VARIANT`です。  
  
-   アパートメント モデル、集計、またはレジストリのライセンス認証を使用するがない、 [CoCreateInstance 関数](http://go.microsoft.com/fwlink/?LinkId=142894)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ICLRAppDomainResourceMonitor インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 アプリケーション ドメインのメモリおよび CPU 使用率を検査するメソッドを提供します。  
  
 [ICLRDomainManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 ホストが初期化プロパティを指定して既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーを指定できるようにします。  
  
 [ICLRGCManager2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 提供、 [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)メソッドにより、ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズに設定する値を超えるホストを`DWORD`です。  
  
 [ICLRMetaHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 CLR の特定のバージョンを返す、インストールされている Clr のすべてを一覧表示、すべてのプロセスのランタイムを一覧表示、アクティブ化インターフェイスを返すおよびアセンブリをコンパイルするために使用する CLR バージョンを検出するメソッドを提供します。  
  
 [ICLRMetaHostPolicy インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 提供、 [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)ポリシーの条件、マネージ アセンブリをバージョン、および構成ファイルに基づいて、CLR インターフェイスを提供するメソッド。  
  
 [ICLRRuntimeInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 バージョン、ディレクトリ、負荷の状態など、特定のランタイムに関する情報を返すメソッドを提供します。  
  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 厳密な名前によるアセンブリの署名の基本的なグローバル静的関数を提供します。 すべての[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)メソッドは、標準の COM Hresult を返します。  
  
 [ICLRStrongName2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Sha-2 グループ (sha-256、sha-384、および sha-512) のセキュリティで保護されたハッシュ アルゴリズムを使用する厳密な名前を作成する機能を提供します。  
  
 [ICLRTask2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 すべての機能を提供、 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)以外の場合はさらに、現在のスレッドで遅延するスレッドの中止できるようにするメソッドを提供します。  
  
## <a name="related-sections"></a>関連項目  
 [サポートされなくなった CLR ホスト インターフェイスおよびコクラス](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 .NET Framework バージョン 1.0 および 1.1 で提供されるホスティング インターフェイスをについて説明します。  
  
 [CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 .NET Framework バージョン 2.0、3.0、および 3.5 で提供されるホスティング インターフェイスについて説明します。  
  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 .NET Framework でのホスティングについて説明します。
