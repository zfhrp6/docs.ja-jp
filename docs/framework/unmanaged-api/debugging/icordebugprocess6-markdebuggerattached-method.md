---
title: ICorDebugProcess6::MarkDebuggerAttached メソッド
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aea837c4973f7a0c157a36c05799536ab528638e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421019"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached メソッド
.NET Framework クラス ライブラリの <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドが `true` を返すように、デバッグ対象の内部状態を変更します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fIsAttached`  
 `true` メソッドが、デバッガーが接続されていることを示す必要がある場合は、<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>。それ以外の場合は、`false`。  
  
## <a name="return-value"></a>戻り値  
 メソッドは、次の表に記載されている値を返す場合があります。  
  
|戻り値|説明|  
|------------------|-----------------|  
|`S_OK`|デバッグ対象は正常に更新されました。|  
|`CORDBG_E_MODULE_NOT_LOADED`|<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドを格納するアセンブリが読み込まれていないか、メタデータの欠落などの他のエラーが原因で認識されません。<br /><br /> このエラーは一般的なもので、問題ありません。 追加のアセンブリを読み込むときに、再度メソッドを呼び出す必要があります。|  
|その他の失敗した `HRESULT` 値。|可能性が高いその他の値は、不適切に動作するデバッガーまたはコンパイラ コンポーネントを示します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugProcess6 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
