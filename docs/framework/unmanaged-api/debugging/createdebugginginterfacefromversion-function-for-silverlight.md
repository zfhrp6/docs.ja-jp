---
title: CreateDebuggingInterfaceFromVersion 関数 (Silverlight 用)
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53571268391011cc1dc0ff112d484e1fa140057f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407715"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a>CreateDebuggingInterfaceFromVersion 関数 (Silverlight 用)
返される共通言語ランタイム (CLR) バージョン文字列を受け入れる、 [CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)、し、対応するデバッガー インターフェイスを返します (通常、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md))。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szDebuggeeVersion`  
 [in]によって返されるデバッグ対象により、CLR のバージョン文字列、 [CreateVersionStringFromModule 関数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)です。  
  
 `ppCordb`  
 [out] COM オブジェクト (`IUnknown`) へのポインターのポインター。 このオブジェクトにキャストされます、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)オブジェクトに返されます。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 `ppCordb` 実装する有効なオブジェクトを参照して、 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)インターフェイスです。  
  
 E_INVALIDARG  
 `szDebuggeeVersion` または `ppCordb` が null です。  
  
 CORDBG_E_DEBUG_COMPONENT_MISSING  
 CLR デバッグに必要なコンポーネントが見つかりません。 つまり、mscordbi.dll または mscordaccore.dll が対象の CoreCLR.dll と同じディレクトリに見つかりませんでした。  
  
 CORDBG_E_INCOMPATIBLE_PROTOCOL  
 mscordbi.dll または mscordaccore.dll が対象の CoreCLR.dll と同じバージョンではありません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 返すことができません、 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)です。  
  
## <a name="remarks"></a>コメント  
 返されるインターフェイスは、対象のプロセス内の CLR にアタッチして CLR が実行しているマネージ コードをデバッグする機能を提供します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** dbgshim.h  
  
 **ライブラリ:** dbgshim.dll  
  
 **.NET framework のバージョン:** 3.5 SP1
