---
title: "CorPinvokeMap 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPinvokeMap
helpviewer_keywords: CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e0771ce54e7e2973525bfcf4aba4c1f7ddf0a52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap 列挙型
PInvoke 呼び出しのオプションを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pmNoMangle`|指定された各メンバー名を使用します。|  
|`pmCharSetMask`|予約済み。|  
|`pmCharSetNotSpec`|予約済み。|  
|`pmCharSetAnsi`|マルチ バイト文字の文字列としての文字列をマーシャ リングします。|  
|`pmCharSetUnicode`|2 バイトの Unicode 文字としての文字列をマーシャ リングします。|  
|`pmCharSetAuto`|対象のオペレーティング システムに適した文字列を自動的にマーシャ リングします。 既定値は Unicode に Windows NT、Windows 2000、Windows XP および Windows Server 2003 ファミリです。既定値は Windows 98 や Windows me では ANSI|  
|`pmBestFitUseAssem`|予約済み。|  
|`pmBestFitEnabled`|ANSI 文字セットで一致がない Unicode 文字の最適マッピングを実行します。|  
|`pmBestFitDisabled`|Unicode 文字の最適マッピングを実行できません。 この場合、すべてのマップできない文字に置き換えられます、'?' です。|  
|`pmBestFitMask`|予約済み。|  
|`pmThrowOnUnmappableCharUseAssem`|予約済み。|  
|`pmThrowOnUnmappableCharEnabled`|相互運用マーシャラーは、マップできない文字を検出したときに、例外をスローします。|  
|`pmThrowOnUnmappableCharDisabled`|相互運用マーシャラーは、マップできない文字を検出したときに例外をスローしません。|  
|`pmThrowOnUnmappableCharMask`|予約されています。|  
|`pmSupportsLastError`|呼び出して、Win32、呼び出し先を許可する`SetLastError`属性付きメソッドから戻る前に機能します。|  
|`pmCallConvMask`|予約されています。|  
|`pmCallConvWinapi`|既定のプラットフォーム呼び出し規約を使用します。 たとえば、Windows では、既定値は`StdCall`では Windows CE .NET`Cdecl`です。|  
|`pmCallConvCdecl`|使用して、`Cdecl`呼び出し規約です。 この場合、呼び出し元は、スタックをクリーンアップします。 これにより、関数を呼び出す`varargs`(つまり、可変個のパラメーターを受け入れる関数)。|  
|`pmCallConvStdcall`|使用して、`StdCall`呼び出し規約です。 この場合、呼び出し先がスタックを消去します。 これは、アンマネージ関数を呼び出すプラットフォーム呼び出しの既定の規則です。|  
|`pmCallConvThiscall`|使用して、`ThisCall`呼び出し規約です。 この場合、最初のパラメーターは、`this`ポインター レジスタ ECX に保存されます。 その他のパラメーターをスタックにプッシュされます。 `ThisCall`呼び出し規約はアンマネージ DLL からエクスポートされたクラスのメソッドの呼び出しに使用します。|  
|`pmCallConvFastcall`|予約済み。|  
|`pmMaxValue`|予約済み。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
