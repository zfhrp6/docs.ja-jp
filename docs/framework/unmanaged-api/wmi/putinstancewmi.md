---
title: "PutInstanceWmi 関数 (アンマネージ API リファレンス)"
description: "PutInstanceWmi 関数を作成または既存のクラスのインスタンスを更新します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutInstanceWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutInstanceWmi
helpviewer_keywords: PutInstanceWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1996103eea87562226537f9aa90dc337c56313c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi 関数
作成するか、既存のクラスのインスタンスを更新します。 インスタンスは、WMI リポジトリに書き込まれます。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>パラメーター

`pInst`    
[in]書き込まれるインスタンスへのポインター。

`lFlags`   
[in]この関数の動作に影響するフラグの組み合わせ。 次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。 

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | かどうか設定、WMI は格納されませんされた修飾子で、 **Amended**フレーバー。 </br> セットと見なされます、このオブジェクトがローカライズされていないとすべての修飾子がある storedwith されていない場合はこのインスタンス。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 存在したり、既に存在する場合は、上書きしない場合は、インスタンスを作成します。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | インスタンスを更新します。 成功するへの呼び出しのインスタンスが存在する必要があります。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | インスタンスを作成します。 インスタンスが既に存在する場合、呼び出しが失敗します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグは、半同期呼び出しがします。 |

`pCtx`  
[in]この値は、通常、`null`です。 ポインターはそれ以外の場合、 [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx)要求されたクラスを提供しているプロバイダーで使用できるインスタンスです。 

`ppCallResult`  
[out]場合`null`、このパラメーターは使用されません。 場合`lFlags`含む`WBEM_FLAG_RETURN_IMMEDIATELY`、関数を直ちに返します`WBEM_S_NO_ERROR`です。 `ppCallResult`パラメーターは、新しいへのポインターを受け取ります[IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx)オブジェクト。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、指定したクラスのインスタンスを更新するアクセス許可がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | このインスタンスをサポートするクラスが正しくありません。 |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null`できないプロパティに指定されました`null`でマークされているいずれかなど、**インデックス**または**not_**修飾子です。 |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | 指定したインスタンスが正しくありません。 (たとえば、呼び出す`PutInstanceWmi`クラスにこの値を返します)。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが正しくありません。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY`フラグが指定されましたが、インスタンスは既に存在します。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`指定された`lFlags`は、インスタンスが存在しません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | リモート プロシージャ コール (RPC) リンクで、現在のプロセスと WMI との間に失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。 |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx)メソッドです。

`PutInstanceWmi`関数のインスタンスを作成して、更新のみの既存のクラスのインスタンスをサポートします。  方法に応じて`pCtx`パラメーターが設定されており、一部またはすべてのインスタンスのプロパティが更新されます。 

ときに、インスタンスを指す`pInst`サブクラスが派生するクラスを担当するすべてのプロバイダーの呼び出し、サブクラスでは、Windows の管理に属しています。 元の成功する必要がありますすべてこれらのプロバイダーの`PutInstanceWmi`の要求に成功します。 階層の最上位のクラスをサポートするプロバイダーが呼び出されます。 呼び出し元の order が最上位のクラスのサブクラスを続行し、Windows 管理によって示されるインスタンスを所有しているクラスのプロバイダーに到達するまで、上から下へ進みます`pInst`です。
Windows の管理には、インスタンスの子クラスのいずれかのプロバイダーは呼び出されません。 

アプリケーションは、クラスの階層構造に属するインスタンスを更新する必要がありますと、`pInst`パラメーターは、変更するプロパティを含むインスタンスを指す必要があります。 つまり、ターゲット インスタンスが属しているを検討**ClassB**です。 **ClassB**から派生したインスタンス**ClassA**、および**ClassA**プロパティを定義**PropA**です。 アプリケーションがの値を変更するか**PropA**で、 **ClassB**に設定する必要がありますインスタンス、`pInst`のインスタンスではなく、そのインスタンスに**ClassA**.

呼び出す`PutInstanceWmi`抽象クラスのインスタンスでは許可されていません。

呼び出して追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
