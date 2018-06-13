---
title: IHostAssemblyStore::ProvideAssembly メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e32d48931177a42dd14092b4052370764a217abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440364"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly メソッド
によって参照されているアセンブリへの参照を取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)から返された[ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)です。 共通言語ランタイム (CLR) を呼び出す`ProvideAssembly`一覧に表示されていないアセンブリごとにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pBindInfo`  
 [in]ポインター、 [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)ホストを使用して、任意のバージョン管理ポリシーの存在の有無を含め、特定のバインド特性を判別するインスタンスにバインドするアセンブリとします。  
  
 `pAssemblyId`  
 [out]この要求されたアセンブリの一意の識別子へのポインター`IStream`です。  
  
 `pHostContext`  
 [out]プラットフォームがなくても要求されたアセンブリの証拠の決定に使用されるホストに固有のデータへのポインターでは、呼び出しが発生します。 `pHostContext` 対応する、<xref:System.Reflection.Assembly.HostContext%2A>マネージ プロパティ<xref:System.Reflection.Assembly>クラスです。  
  
 `ppStmAssemblyImage`  
 [out]アドレスへのポインター、`IStream`ポータブル実行可能 (PE) イメージを読み込む、またはアセンブリが見つからなかった場合は null を格納しています。  
  
 `ppStmPDB`  
 [out]アドレスへのポインター、`IStream`を格納しているプログラムのデバッグ (PDB) の情報、または null 場合、.pdb ファイルが見つかりませんでした。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|COR_E_FILENOTFOUND (0X80070002)|要求されたアセンブリが見つかりませんでした。|  
|E_NOT_SUFFICIENT_BUFFER|によって指定されたバッファー サイズ`pAssemblyId`に返す必要が、ホストの識別子を保持するのに十分ではありません。|  
  
## <a name="remarks"></a>コメント  
 Id 値が返される`pAssemblyId`ホストによって指定します。 識別子は、プロセスの有効期間内で一意である必要があります。 CLR は、この値をストリームの一意の識別子として使用します。 値に対して各値をチェック`pAssemblyId`を他の呼び出しによって返される`ProvideAssembly`です。 場合は、ホストは、同じを返します`pAssemblyId`別の値`IStream`CLR では、そのストリームの内容が既にマップされているかどうかを確認します。 場合は、ランタイムは新しい 1 つのマッピングではなく、イメージの既存のコピーを読み込みます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
