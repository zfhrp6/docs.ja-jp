---
title: "BlessIWbemServicesObject 関数 (アンマネージ API リファレンス)"
description: "BlessIWbemServicesObject 関数では、ユーザーの資格情報が IWbemServices オブジェクトへのアクセスを許可するかどうかを示します"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2430358e5ea21468c2e975c2a26f20fe801ee546
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject 関数
ユーザーの資格情報が、指定されたアクセスを許可するかどうかを示す[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)オブジェクト。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a>パラメーター

`pIWbemServices`  
[in]WMI サービス オブジェクトへのポインター。

`strUser`  
[in]ユーザー名。

`strPassword`  
[in]関連付けられているパスワード`strUser`です。

`strAuthority`[in]ユーザーのドメイン名。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

`impLevel`[in]権限借用レベルです。

`authnLevel`[in]承認レベル。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WinError.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | 1 つまたは複数の引数が無効です。 |
| `E_POINTER` | 0x80004003 | `pIWbemServices` は `null` です。 | 
| `E_FAIL` | 0x80000008 | 不明なエラーが発生しました。 |
| `E_OUTOFMEMORY` | 0x80000002 | 操作の実行に使用できるは、メモリ不足です。 | 
| `S_OK` | 0 | 関数呼び出しに成功しました。 | 

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
