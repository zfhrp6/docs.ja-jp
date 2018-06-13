---
title: イベントとコールバック
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90cc40024de627f151a4d0df879a65e5900004b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573634"
---
# <a name="events-and-callbacks"></a>イベントとコールバック
コールバックでは、フレームワークがデリゲートからのユーザー コードにコールバックする機能拡張ポイントです。 これらのデリゲートは、メソッドのパラメーターを通じて通常フレームワークに渡されます。  
  
 イベントは、デリゲート (イベント ハンドラー) を提供するための便利で一貫した構文をサポートするコールバックの特殊なケースです。 さらに、Visual Studio のステートメント入力候補およびデザイナーは、イベント ベースの Api を使用してヘルプを提供します。 (を参照してください[イベント デザイン](../../../docs/standard/design-guidelines/event.md))。  
  
 **✓ を検討してください**コールバックを使用して、フレームワークによって実行されるカスタム コードを提供できるようにします。  
  
 **✓ を検討してください**イベントを使用したオブジェクト指向設計を理解することがなくてもフレームワークの動作をカスタマイズできるようにします。  
  
 **✓ しないで**幅広い開発者になじみのあるは、ステートメント入力候補の Visual Studio と統合されたために、イベントを単純なコールバックよりも優先されます。  
  
 **避け x**パフォーマンス重視の Api でのコールバックを使用します。  
  
 **✓ は**新しい`Func<...>`、 `Action<...>`、または`Expression<...>`コールバックで Api を定義するときに、カスタム デリゲートではなく型です。  
  
 `Func<...>` および`Action<...>`汎用デリゲートを表します。 `Expression<...>` コンパイルと、その後もできますが、実行時に呼び出されることができますを表す関数定義シリアル化およびリモート プロセスに渡されます。  
  
 **✓ しないで**を測定しを使用するパフォーマンスの影響について理解する`Expression<...>`、使用する代わりに`Func<...>`と`Action<...>`デリゲート。  
  
 `Expression<...>` 型はほとんどの場合と論理的に等価に`Func<...>`と`Action<...>`デリゲート。 主な違いは、デリゲートがローカル処理のシナリオで使用するものでは、式がある場合と役に立つとリモート プロセスまたはコンピューターで式を評価することを意図しています。  
  
 **✓ しないで**するデリゲートを呼び出すことによって実行している任意のコードを理解し、セキュリティ、正確性、および互換性への影響を与える可能性です。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
