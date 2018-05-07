---
title: IHostMemoryManager::VirtualQuery メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68a9d6ad7470ffaf1143a4a8e3134f20edb9e3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery メソッド
対応する Win32 関数の論理ラッパーとして機能します。 Win32 実装`VirtualQuery`呼び出しプロセスの仮想アドレス空間内のページの範囲に関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `lpAddress`  
 [in]クエリを実行する仮想メモリ内のアドレスへのポインター。  
  
 `lpBuffer`  
 [out]指定したメモリ領域に関する情報を格納する構造体へのポインター。  
  
 `dwLength`  
 [in]バッファーのバイト単位のサイズを`lpBuffer`を指します。  
  
 `pResult`  
 [out]情報バッファーによって返されたバイト数へのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
  
## <a name="remarks"></a>コメント  
 `VirtualQuery` 呼び出し元のプロセス仮想アドレス空間内のページの範囲に関する情報を提供します。 この実装の値を設定する、`pResult`のバイト数のパラメーター情報バッファーに返され、HRESULT 値を返します。 Win32 で`VirtualQuery`関数、戻り値は、バッファー サイズ。 詳細については、Windows プラットフォームのドキュメントを参照してください。  
  
> [!IMPORTANT]
>  オペレーティング システムの実装`VirtualQuery`デッドロックが発生しないと、ユーザー コードで中断されているランダムなスレッドで完了するまで実行できます。 このメソッドのホストされているバージョンを実装する場合は、注意深くを使用します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
