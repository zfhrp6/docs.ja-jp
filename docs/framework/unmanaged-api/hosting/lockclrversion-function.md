---
title: LockClrVersion 関数
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6956d73be0380baef96d94584f007e0683331784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446090"
---
# <a name="lockclrversion-function"></a>LockClrVersion 関数
により、ホストがプロセス内で明示的に CLR を初期化する前に使用する共通言語ランタイム (CLR) のバージョンを決定します。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `hostCallback`  
 [in]初期化時に CLR によって呼び出される関数。  
  
 `pBeginHostSetup`  
 [in]初期化の CLR を通知するためにホストによって呼び出される関数を開始しています。  
  
 `pEndHostSetup`  
 [in]初期化の CLR を通知するためにホストによって呼び出される関数が完了しました。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値に加え、WinError.h で定義されている標準の COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|1 つ以上の引数が null です。|  
  
## <a name="remarks"></a>コメント  
 ホスト呼び出し`LockClrVersion`CLR を初期化する前にします。 `LockClrVersion` 型のコールバックをすべての 3 つのパラメーターを受け取る[FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)です。 この種類の定義は次のとおりです。  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 次の手順は、ランタイムの初期化時に発生します。  
  
1.  ホスト呼び出し[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)または他のランタイム初期化関数のいずれか。 または、ホストは、COM オブジェクトのアクティブ化を使用してランタイムを初期化する可能性があります。  
  
2.  ランタイムがで指定された関数を呼び出す、`hostCallback`パラメーター。  
  
3.  指定された関数`hostCallback`次の一連の呼び出しを使用します。  
  
    -   指定された関数、`pBeginHostSetup`パラメーター。  
  
    -   `CorBindToRuntimeEx` (または別のランタイム初期化関数)。  
  
    -   [Iclrruntimehost::sethostcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)です。  
  
    -   [Iclrruntimehost::start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)です。  
  
    -   指定された関数、`pEndHostSetup`パラメーター。  
  
 すべての呼び出し`pBeginHostSetup`に`pEndHostSetup`1 つのスレッドまたはファイバーは、同じ論理スタックに対して実行する必要があります。 このスレッドは、基になるスレッドと異なる場合が`hostCallback`と呼びます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
