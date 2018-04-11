---
title: フレームワーク デザインのガイドライン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c48b3cbaae4155a894ba77263505b2ca85238427
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="framework-design-guidelines"></a>フレームワーク デザインのガイドライン
このセクションでは、ライブラリを拡張し、.NET Framework との対話をデザインするためのガイドラインを示します。 目標は、ライブラリのデザイナーが開発に使用するプログラミング言語に関係なく、統一されたプログラミング モデルを提供することで API の一貫性と使いやすさを確認するためです。 クラスと、.NET Framework を拡張するコンポーネントを開発する際に、これらのデザイン ガイドラインに従うことをお勧めします。 一貫性のないライブラリ デザインが悪影響を及ぼす開発者の生産性に影響し、導入を行わないましょう。  
  
 ガイドラインは、語句で始まる簡単な推奨事項として編成`Do`、 `Consider`、 `Avoid`、および`Do not`です。 次のガイドラインについては、クラス ライブラリのデザイナーのさまざまなソリューション間のトレードオフを理解するためものです。 適切なライブラリ デザインではこれらのデザイン ガイドラインに違反することが必要な状況である可能性があります。 このような場合はまれで、意思決定の理由を明確かつ説得力のあることが重要です。  
  
 次のガイドラインは、ブックからの抜粋です*Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン*は Cwalina Brad Abrams では、します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 アセンブリ、名前空間、型、およびクラス ライブラリ内のメンバーの名前付けのガイドラインを提供します。  
  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)  
 静的な抽象クラス、インターフェイス、列挙型、構造体、およびその他の種類を使用するためのガイドラインを提供します。  
  
 [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)  
 デザインおよびプロパティ、メソッド、コンス トラクター、フィールド、イベント、演算子、およびパラメーターを使用するためのガイドラインを提供します。  
  
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 イベント、仮想メンバー、およびコールバック関数を使用して、サブクラスなどの機能拡張機構について説明し、フレームワークの要件に最適なメカニズムを選択する方法を説明します。  
  
 [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)  
 デザイン、スロー、および例外のキャッチのデザイン ガイドラインをについて説明します。  
  
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 配列、属性、およびコレクションなどの一般的な型を使用して、シリアル化のサポート、等値演算子のオーバー ロードに関するガイドラインについて説明します。  
  
 [共通デザイン パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 選択して、依存関係プロパティと、dispose パターンの実装のガイドラインを提供します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [概要](../../../docs/framework/get-started/overview.md)  
 [.NET Framework のロードマップ](http://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [開発ガイド](../../../docs/framework/development-guide.md)
