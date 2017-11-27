---
title: "CreateDebuggingInterfaceFromVersion 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords: CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cc352603ef1c3610edf99f7bdd877c6bb0e5d9fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion 関数
作成、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)オブジェクトが指定されたバージョン情報に基づいています。  
  
 この関数は廃止されていますが、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。 代わりに、共通言語ランタイム (CLR) 2.0 用のインターフェイスを取得する次のように使用します。、 [iclrruntimeinfo::getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)メソッド クラス識別子 CLSID_CLRDebuggingLegacy と IID_ICorDebug インターフェイス識別子を指定します。 CLR 4 をインターフェイスを取得するか、後で、呼び出しを[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数し、クラス識別子 CLSID_CLRDebugging と IID_ICLRDebugging インターフェイス識別子を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `iDebuggerVersion`  
 [in]バージョン`ICorDebug`はデバッガーで想定します。 参照してください、 [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)有効な値を列挙します。  
  
 `szDebuggeeVersion`  
 [in]デバッグするには、アプリケーションまたはプロセスに関連付けられている、共通言語ランタイム バージョンです。 参照してください、 [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)または[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)については、この値を取得するメソッド。  
  
 `ppCordb`  
 [out]ポインターを受け取る場所、`ICorDebug`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値だけでなく WinError.h ファイルで定義されている標準の COM エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`szDebuggeeVersion`または`ppCordb`が null の場合、またはバージョン文字列が正しくありません。|  
  
## <a name="remarks"></a>コメント  
 `szDebuggeeVersion`パラメーターが MSCorDbi.dll の対応するバージョンにマップします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [推奨されなくなった CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
