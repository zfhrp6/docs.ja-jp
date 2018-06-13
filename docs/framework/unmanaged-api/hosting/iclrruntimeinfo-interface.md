---
title: ICLRRuntimeInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc8225b6612c7bf07d220b20d515f64a346b9691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436469"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo インターフェイス
バージョン、ディレクトリ、および負荷の状態を含む特定の共通言語ランタイム (CLR) に関する情報を返すメソッドを提供します。 また、このインターフェイスは、ランタイムを初期化せずランタイム固有の機能を提供します。 ランタイムの相対が含まれている[LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)メソッドは、ランタイム モジュール固有[GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)メソッド、およびを介してランタイムに用意されているインターフェイス、 [GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)メソッドです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|すべてレガシー CLR バージョン 2 のアクティブ化ポリシーを決定するためには、このランタイムにバインドします。|  
|[GetDefaultStartupFlags メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|CLR スタートアップ フラグとホストの構成ファイルを取得します。|  
|[GetInterface メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|現在のプロセスに CLR を読み込んで、ランタイム、インターフェイス ポインターをなど返します[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)、 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)と[IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)です。 このメソッドはすべて、`CorBindTo*`関数。|  
|[GetProcAddress メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|このインターフェイスに関連付けられた CLR からエクスポートされた、指定された関数のアドレスを取得します。 このメソッドは、 [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)メソッドです。|  
|[GetRuntimeDirectory メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|このインターフェイスに関連付けられている CLR のインストール ディレクトリを取得します。 このメソッドは、 [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)メソッドです。|  
|[GetVersionString メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|関連付けられている共通言語ランタイム (CLR) バージョン情報を取得する指定された[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスです。 このメソッドは、 [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)と[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)メソッドです。|  
|[IsLoadable メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|このインターフェイスに関連付けられているランタイムを考慮に入れて、現在のプロセスに読み込めるかどうかを示す他のランタイムをプロセスに既に読み込まれている可能性があります。|  
|[IsLoaded メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|CLR に関連付けられているかどうかを示す、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスが、プロセスに読み込まれます。|  
|[IsStarted メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|かどうか、CLR に関連付けられていることを示します、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスが開始されました。|  
|[LoadErrorString メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|指定されたカルチャに適切なエラー メッセージには、HRESULT 値を変換します。 このメソッドは、 [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)と[LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)メソッドです。|  
|[LoadLibrary メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|によって表される CLR の framework ディレクトリからライブラリを読み込み、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)インターフェイスです。 このメソッドは、 [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)メソッドです。|  
|[SetDefaultStartupFlags メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|CLR スタートアップ フラグとホストの構成ファイルを設定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
