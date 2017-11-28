---
title: "ClrCreateManagedInstance 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: ClrCreateManagedInstance
helpviewer_keywords: ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d27a881f84121f0d096eae7c693dec5b674caec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance 関数
指定したマネージ型のインスタンスを作成します。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。 COM のアクティブ化を使用して、マネージ型のインスタンスを作成するか、ホストを使用して (を参照してください[CLR をホストしている .NET Framework 4 および 4.5 で追加されたインターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md))。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pTypeName`  
 [in]要求されているインスタンスの型の名前へのポインター。  
  
 `riid`  
 [in]`IID`要求されているインスタンスの型のです。  
  
 `ppObject`  
 [out]呼び出し元によって要求されたマネージ型のインスタンスへのポインターへのポインター。  
  
## <a name="remarks"></a>コメント  
 共通言語ランタイムは、プロセスに既に読み込まれている必要があります。 たとえば、読み込むことができますに呼び出しを使用して、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)関数の前に、`ClrCreateManagedInstance`関数が呼び出されます。 ランタイムが読み込まれていない場合`ClrCreateManagedInstance`最初に、ランタイムの v1.0.3705 の読み込みを試みます。 失敗した場合、ランタイムの最新バージョンをロードしようとします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [推奨されなくなった CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
