---
title: ICorDebugAppDomain::GetObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f528bcef7d06b503b1ee9d7bd4a61d3d3e9672
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406521"
---
# <a name="icordebugappdomaingetobject-method"></a>ICorDebugAppDomain::GetObject メソッド
共通言語ランタイム (CLR) のアプリケーション ドメインへのインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppObject`  
 [out]CLR のアプリケーション ドメインを表す ICorDebugValue インターフェイス オブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 マネージ場合<xref:System.AppDomain?displayProperty=nameWithType>オブジェクトは、このアプリケーション ドメインの構築されていない、メソッドが返されます`S_FALSE`配置`NULL`で`*ppObject`です。  
  
## <a name="remarks"></a>コメント  
 プロセス内の各アプリケーション ドメインは、管理されている必要があります<xref:System.AppDomain?displayProperty=nameWithType>を表すそのランタイム内のオブジェクト。 この関数は、管理に対応する ICorDebugValue インターフェイス オブジェクトを取得します。<xref:System.AppDomain?displayProperty=nameWithType>オブジェクト。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
