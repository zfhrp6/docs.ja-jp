---
title: IHostMemoryManager::VirtualFree メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 063ddd0bfa1734d43f90b4680166c21b80f5cc05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439108"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree メソッド
対応する Win32 関数の論理ラッパーとして機能します。 Win32 実装`VirtualFree`解放、デコミット、またはを解放し、呼び出し元プロセスの仮想アドレス空間内のページの領域をデコミットします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `lpAddress`  
 [in]解放される仮想メモリ ページの基本アドレスへのポインター。  
  
 `dwSize`  
 [in]\(バイト単位) が解放される領域のサイズ。  
  
 `dwFreeType`  
 [in]解放操作の種類。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`VirtualFree` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|HOST_E_INVALIDOPERATION|ホストが割り当てられていないメモリを解放しようとしました。|  
  
## <a name="remarks"></a>コメント  
 `VirtualFree` 関連付けられている仮想メモリ ページの解放、`lpAddress`事前に呼び出したを通じてパラメーター、 [ihostmemorymanager::virtualalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)関数。 ホストが割り当てられていないメモリを解放する試行は、HOST_E_INVALIDOPERATION を返す必要があります。  
  
 セマンティクスは次の Win32 実装のものと同じ`VirtualFree`です。 詳細については、Windows プラットフォームのドキュメントを参照してください。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [IHostMalloc インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
