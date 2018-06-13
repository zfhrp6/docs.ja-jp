---
title: s_isDebuggerCheckDisabledForTestPurposes フィールド
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
robots: noindex,nofollow
ms.openlocfilehash: fbbd8d33ea163efaad1417ab4a1435df729e4897
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752209"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes フィールド

このプライベート フィールドで、`System.Windows.Diagnostics.VisualDiagnostics`クラスは、内部のアクティブなデバッガーのチェックを実行するかどうかを決定する Visual Studio によって使用されます。

## <a name="syntax"></a>構文
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  API で、`System.Windows.Diagnostics.VisualDiagnostics`クラスは、デバッガーの下で、アプリケーションが実行されている場合にのみ使用できます。 設定`s_isDebuggerCheckDisabledForTestPurposes`に`true`デバッガーの外部の Api にアクセスします。  
>   
>  Microsoft は、どのような状況下で、実稼働アプリケーションでこのフィールドの使用をサポートしていません。  

## <a name="requirements"></a>要件

**Namespace:** <xref:System.Windows.Diagnostics>

**アセンブリ:** PresentationCore.dll) の「PresentationCore

**.NET framework のバージョン:** 4.6 以降の利用可能です。
