---
title: "s_isDebuggerCheckDisabledForTestPurposes フィールド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.workload:
- dotnet
ms.openlocfilehash: 67da38d958d153ebe526f298785b39afb7be6513
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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

## <a name="requirements"></a>必要条件

**Namespace:**<xref:System.Windows.Diagnostics>

**アセンブリ:** PresentationCore.dll) の「PresentationCore

**.NET framework のバージョン:** 4.6 以降の利用可能です。
