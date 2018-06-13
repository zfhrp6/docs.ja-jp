---
title: IHostMemoryManager::VirtualAlloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe54aed47d240be37ab9dbc5381235c4e962f1f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440315"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc メソッド
対応する Win32 関数の論理ラッパーとして機能します。 Win32 実装`VirtualAlloc`予約または呼び出し元のプロセス仮想アドレス空間内のページの領域をコミットします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAddress`  
 [in]割り当てる領域の開始アドレスへのポインター。  
  
 `dwSize`  
 [in]領域のバイト単位のサイズ。  
  
 `flAllocationType`  
 [in]メモリの割り当ての種類。  
  
 `flProtect`  
 [in]割り当てられるページの領域のメモリ保護します。  
  
 `dwCriticalLevel`  
 [in][EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)割り当てエラーの影響を示す値。  
  
 `ppMem`  
 [out]割り当てられたメモリは、または要求を処理できなかった場合は null の開始アドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|E_OUTOFMEMORY|十分なメモリ割り当て要求を完了できませんでした。|  
  
## <a name="remarks"></a>コメント  
 呼び出すことによって、プロセスのアドレス空間内の領域を予約する`VirtualAlloc`です。 `pAddress`パラメーターには、必要なメモリ ブロックの開始アドレスが含まれています。 通常、このパラメーターは設定を null にします。 オペレーティング システムをプロセスに使用可能な空きアドレス範囲のレコードを保持します。 A`pAddress`値は null に適した場所に、領域を予約するシステムに指示します。 また、メモリ ブロックの特定の開始アドレスを指定できます。 どちらの場合も、出力パラメーター`ppMem`が割り当てられたメモリへのポインターとして返されます。 関数自体では、HRESULT 値を返します。  
  
 Win32`VirtualAlloc`関数はありません、`ppMem`パラメーター、し、代わりに割り当てられたメモリへのポインターを返します。 詳細については、Windows プラットフォームのドキュメントを参照してください。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
