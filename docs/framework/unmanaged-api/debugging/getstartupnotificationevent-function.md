---
title: "GetStartupNotificationEvent 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 809f34d265e0a1677d8b7fc78515b20df7353968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent 関数
指定された対象プロセスに読み込まれている任意の共通言語ランタイム (CLR: Common Language Runtime) によって通知されるイベント ハンドルを作成または開きます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `debuggeePID`  
 [in] 受信する CLR スタートアップ通知の送信元である対象プロセスのプロセス識別子。  
  
 `phStartupEvent`  
 [out] スタートアップ時に CLR によって通知されるハンドルへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 スタートアップ通知イベントに対するハンドルを正常に取得しました。  
  
 E_INVALIDARG  
 `phStartupEvent` が nullであるか、または `debuggeePID` が現在実行されているプロセスを参照していません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 スタートアップ通知イベントに対するハンドルを取得できません。  
  
## <a name="remarks"></a>コメント  
 Windows オペレーティング システムでは、`debuggeePID` が OS プロセス識別子に対応づけられます。  
  
 イベントは、通知元の CLR によってマネージ コードが実行される前に通知されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** dbgshim.h  
  
 **ライブラリ:** dbgshim.dll  
  
 **.NET framework のバージョン:** 3.5 SP1
