---
title: "CloneEnumWbemClassObject 関数 (アンマネージ API リファレンス)"
description: "CloneEnumWbemClassObject 関数は、列挙子の論理コピーを作成します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: CloneEnumWbemClassObject
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: CloneEnumWbemClassObject
helpviewer_keywords: CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a4103a0103a334a0e5eace32d8fcf1b365917b8
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject 関数
列挙体の現在位置を保持、列挙子の論理コピーを作成します。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```  

## <a name="parameters"></a>パラメーター

`ppEnum`  
[out]新しいへのポインターを受け取る[IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx)です。

`authLevel`  
[in]承認レベル。

`impLevel`[in]権限借用レベルです。

`pCurrentEnumWbemClassObject`  
[out]ポインター、 [IEnumWbemClassObject](https://msdn.microsoft.com/library/aa390857(v=vs.85).aspx)クローンを作成するインスタンス。

`strUser`   
[in]ユーザー名。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

`strPassword`   
[in]パスワードです。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

`strAuthority`   
[in]ユーザーのドメイン名。 参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 十分なメモリが使用可能な操作を完了します。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx)メソッドです。

このメソッドは、「最適な」コピーのみです。 多くの CIM オブジェクトの動的な性質が新しい列挙子がソースの列挙子と同じオブジェクトのセットを列挙できません。  

呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="example"></a>例

例については、次を参照してください。、 [IEnumWbemClassObject::Clone](https://msdn.microsoft.com/library/aa390859(v=vs.85).aspx)メソッドです。

## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
