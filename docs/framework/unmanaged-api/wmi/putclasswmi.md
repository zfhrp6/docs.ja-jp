---
title: "PutClassWmi 関数 (アンマネージ API リファレンス)"
description: "PutClassWmi 関数は、新しいクラスを作成または既存のものを更新します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutClassWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutClassWmi
helpviewer_keywords: PutClassWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dda7dc4d71b65c8b031f2dca459bd282eef1f270
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="putclasswmi-function"></a>PutClassWmi 関数
新しいクラスを作成または既存のものを更新します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>パラメーター

`pObject`    
[in]有効なクラス定義へのポインター。 すべての必要なプロパティ値を持つ正しく初期化する必要があります。

`lFlags`   
[in]この関数の動作に影響するフラグの組み合わせ。 次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。 

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 場合設定、WMI では、修正済みのフレーバーで、修飾子は保存されません。 </br> セットと見なされます、このオブジェクトがローカライズされていないとすべての修飾子がある storedwith されていない場合はこのインスタンス。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 存在したり、既に存在する場合は、上書きしない場合は、クラスを作成します。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | クラスを更新します。 クラスは、呼び出しの成功に存在する必要があります。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | クラスを作成します。 クラスが既に存在する場合、呼び出しが失敗します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグは、半同期呼び出しがします。 |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | 呼び出すときに、プッシュ プロバイダーはこのフラグを指定する必要があります`PutClassWmi`をこのクラスが変更されたことを示します。 |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | 派生クラスを持たないとそのクラスのインスタンスがない場合に更新するクラスを使用します。 更新を実行できます常に、変更の説明の修飾子など、重要でない修飾子に場合。 クラスのインスタンスには、または変更は、重要な修飾子には、更新プログラムは失敗します。 |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | 変更には、子のクラスとの競合は発生しません限り、子クラスがある場合でも、クラスの更新プログラムを許可します。 たとえば、このフラグは、子クラスのいずれかで記述されていない基底クラスに追加する新しいプロパティを使用できます。 クラスのインスタンスが存在する場合、更新は失敗します。 |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | 競合する子クラスが存在する場合は、クラスの更新プログラムを強制的にします。 たとえば、このフラグでは、クラス修飾子は、子クラスの定義し、基本クラスの既存の 1 つと競合する同じ区切り記号を追加しようとする場合、更新プログラムが強制されます。 強制モードでは、子クラスで競合する修飾子を削除することによって tis 競合を解決します。 |

`pCtx`  
[in]この値は、通常、`null`です。 ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求されたクラスを提供しているプロバイダーで使用できるインスタンスです。 

`ppCallResult`  
[out]場合`null`、このパラメーターは使用されません。 場合`lFlags`含む`WBEM_FLAG_RETURN_IMMEDIATELY`、関数を直ちに返します`WBEM_S_NO_ERROR`です。 `ppCallResult`パラメーターは、新しいへのポインターを受け取ります[IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx)オブジェクト。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、作成またはクラスを変更する権限がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | 指定したクラスが正しくありません。 通常、これが示す`pObject`インスタンス オブジェクトを指定します。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | 指定されたクラス名が正しくありません。 |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | サブクラスを無効にする変更を加えるしようとしました。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY`フラグが指定されましたが、クラスが既に存在します。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`指定された`lFlags`クラスが見つかりません。 |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | クラスに必要なプロパティがすべて設定されています。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemServices::PutClass](https://msdn.microsoft.com/library/aa392113(v=vs.85).aspx)メソッドです。

ユーザーは、アンダー スコア chacater で開始または終了する名前を持つクラスを作成しない場合があります。

呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
