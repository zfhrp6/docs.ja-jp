---
title: CoreResponseData.m_StatusCode フィールド
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_StatusCode
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 53338c75d31cef3ab89879632710dba3e52091ad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751910"
---
# <a name="coreresponsedatamstatuscode-field"></a>CoreResponseData.m\_StatusCode フィールド

`CoreResponseData.m_StatusCode` <xref:System.Net.HttpStatusCode>応答のステータスを含むです。

## <a name="syntax"></a>構文
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> この API は、コード内で直接使用するものではありません。 代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。 参照してください[DiagnosticSource ユーザーズ ガイド 』](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)です。
> 
> Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。

## <a name="requirements"></a>要件

**Namespace:** <xref:System.Net>

**アセンブリ:** システム (System.dll)

**.NET framework のバージョン:** 2.0 から利用可能です。
