---
title: IHostAssemblyStore::ProvideModule メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b604e1d7fc3d3c8adf7d95bd95843bc0110dbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440019"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule メソッド
アセンブリとリンク (ではありません、埋め込み) 内のモジュール リソース ファイルを解決します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pBindInfo`  
 [in]ポインター、 [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) 、要求されたモジュールを記述するインスタンス<xref:System.AppDomain>アセンブリ、およびモジュールの名前。  
  
 `pdwModuleId`  
 [out]一意の識別子へのポインター、`IStream`読み込まれたモジュールを含むです。  
  
 `ppStmModuleImage`  
 [out]アドレスへのポインター、`IStream`オブジェクト、読み込まれるポータブル実行可能 (PE) イメージが含まれていますか、モジュールが見つからなかった場合は null です。  
  
 `ppStmPDB`  
 [out]アドレスへのポインター、`IStream`オブジェクトを要求されたモジュールのデバッグ (PDB) 情報をプログラムを含むまたは null の場合、.pdb ファイルが見つかりませんでした。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ProvideModule` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|COR_E_FILENOTFOUND (0X80070002)|要求されたアセンブリまたはリンクされたリソースを配置できませんでした。|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` ホストを返す必要がある識別子を格納するのに十分な大きさがないです。|  
  
## <a name="remarks"></a>コメント  
 Id 値が返される`pdwModuleId`ホストによって指定します。 識別子は、プロセスの有効期間内で一意である必要があります。 CLR は、この値を関連付けられているストリームの一意識別子として使用します。 値に対して各値をチェック`pAssemblyId`への呼び出しによって返される[ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)の値に対して`pdwModuleId`を他の呼び出しによって返される`ProvideModule`です。 別のホストが同じ識別子の値を返す場合`IStream`CLR では、そのストリームの内容が既にマップされているかどうかを確認します。 場合は、CLR は、新しいものをマップする代わりにイメージの既存のコピーを読み込みます。 したがって、識別子も重複していないから返されたアセンブリ識別子を持つ`ProvideAssembly`します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
