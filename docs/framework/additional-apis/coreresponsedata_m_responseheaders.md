---
title: "CoreResponseData.m_ResponseHeaders フィールド"
ms.date: 01/29/2018
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.author: stwhi
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: eaece5bfe9cda7d35905ecd7e1da503ec11faf9c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="coreresponsedatamresponseheaders-field"></a>CoreResponseData.m\_ResponseHeaders フィールド

`CoreResponseData.m_ResponseHeaders`<xref:System.Net.WebHeaderCollection>のサーバーの応答に関連付けられたヘッダー。

## <a name="syntax"></a>構文
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> この API は、コード内で直接使用するものではありません。 代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。 参照してください[DiagnosticSource ユーザーズ ガイド 』](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)です。
> 
> Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**Namespace:**<xref:System.Net>

**アセンブリ:**システム (System.dll)

**.NET framework のバージョン:** 2.0 から利用可能です。
