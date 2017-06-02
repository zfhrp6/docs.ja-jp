---
title: "追加のクラス ライブラリと API | Microsoft Docs"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: b53b8acc2a6c56db6a9d8a9b7c685a2d400a53e1
ms.openlocfilehash: 34815268b707aa70d174a1bbc04c32276db8412d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/02/2017

---

# <a name="additional-class-libraries-and-apis"></a>追加のクラス ライブラリと API

.NET Framework は、絶えず進化を続けています。クロスプラットフォーム開発を強化するために、またはお客様にいち早く新しい機能を紹介するために、マイクロソフトは新機能のアウトオブバウンド (OOB) をリリースします。 ここでは、ドキュメントが用意されている OOB プロジェクトの一覧を示します。  
  
さらに、いくつかのライブラリは、特定のプラットフォームまたは .NET Framework の実装を対象にしています。 たとえば、<xref:System.Text.CodePagesEncodingProvider> クラスを使用すると、.NET Framework で開発した UWP アプリでコード ページ エンコーディングを使用できるようになります。 ここでは、これらのライブラリの一覧も示します。  
  
## <a name="oob-projects"></a>OOB プロジェクト
  
| プロジェクト | 説明 |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | スレッド セーフであり、内容が変更されないことが保証されているコレクションを提供します。 |
| <xref:System.Net.Http.WinHttpHandler> | Windows の WinHTTP インターフェイスに基づいた <xref:System.Net.Http.HttpClient> のメッセージ ハンドラーを提供します。 |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | SIMD ハードウェア ベースのアクセラレータを利用できるベクター型のライブラリを提供します。| 
| <xref:System.Threading.Tasks.Dataflow> | TPL データフロー ライブラリはデータ フロー コンポーネントを提供し、同時実行対応アプリケーションの堅牢性を強化します。 |  

## <a name="platform-specific-libraries"></a>プラットフォーム固有のライブラリ
  
| プロジェクト | 説明 |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <xref:System.Text.EncodingProvider> クラスを拡張し、ユニバーサル Windows プラットフォームを対象とするアプリでコード ページ エンコーディングを使用できるようにします。 |  
  
## <a name="private-apis"></a>プライベート API  

この API は製品インフラストラクチャをサポートします。コードから直接使用することはできません。  
  
| API 名 |  
| -------- |  
| [s_isDebuggerCheckDisabledForTestPurposes フィールド](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |  
| [DataMemberFieldEditor クラス](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |  
| [DataMemberListEditor クラス](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |  
  
## <a name="see-also"></a>関連項目

[NET Framework および特別なリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

