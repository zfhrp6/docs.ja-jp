---
title: "例外のスロー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2c1fc02b64a494220070a1cfed928b616e4970c0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="exception-throwing"></a>例外のスロー
このセクションで説明されている例外スローのガイドラインでは、実行エラーの意味を適切な定義が必要です。 メンバーが実行できないときに実行エラーが発生する (新機能、メンバー名のとおり) を実行するように設計します。 たとえば場合、`OpenFile`メソッドは、呼び出し元に、開いているファイル ハンドルを返すことはできません、実行エラーと見なされるとします。  
  
 ほとんどの開発者は、0 または null 参照による除算などの使用状況のエラーの例外の使用に慣れてになっています。 Framework では、例外は、実行エラーを含む、すべてのエラー条件に使用されます。  
  
 **X しないで**エラー コードを返します。  
  
 例外は、フレームワークにエラーを報告の主な手段です。  
  
 **✓ しないで**例外をスローして、実行の失敗を報告します。  
  
 **✓ を検討してください**呼び出すことによって、プロセスを終了して`System.Environment.FailFast`(.NET Framework 2.0 の機能)、コードが安全に実行をさらにはない状況が発生すると、例外をスローする代わりにします。  
  
 **X しないで**可能であれば、コントロールの通常のフローの例外を使用します。  
  
 システム障害、潜在的な競合状態を持つ操作を除くユーザーが例外をスローしないコードを記述できるように、フレームワークの設計者は Api を設計する必要があります。 たとえば、ユーザーが例外をスローしないコードを記述できるようにメンバーを呼び出す前に前提条件を確認する方法を提供することができます。  
  
 別のメンバーの前提条件の確認に使用するメンバーは多くの場合と呼ばれ、テスト担当者を実際に実行するメンバーは、渡ってと呼ばれます。  
  
 場合、テスト担当者渡ってパターンが許容できないパフォーマンス オーバーヘッドを持つことができます。 このような場合、いわゆる Try 解析パターン見なす必要があります (を参照してください[例外とパフォーマンス](../../../docs/standard/design-guidelines/exceptions-and-performance.md)詳細については)。  
  
 **✓ を検討してください**パフォーマンス上の違いの例外をスローします。 1 秒あたり 100 を超える throw レートは、ほとんどのアプリケーションのパフォーマンスに著しい影響を与える可能性があります。  
  
 **✓ しないで**ドキュメントによって公開されている呼び出し可能なメンバー、メンバーの違反のためにスローされる例外すべてではなく、システム障害) コントラクトおよびコントラクトの一部として扱われるようにします。  
  
 コントラクトの一部である例外は、次に 1 つのバージョンから変更しないでください (つまり、例外の種類を変更しないでください、および新しい例外を追加してはならない)。  
  
 **X しないで**かどうか throw をできるパブリック メンバーに基づいてにいくつかのオプションです。  
  
 **X しないで**パブリック メンバーの戻り値として例外を返すをまたは`out`パラメーター。  
  
 それらをスローする代わりにパブリック Api から例外を返す例外ベースのエラー報告の利点の多くを無効にします。  
  
 **✓ を検討してください**例外ビルダー メソッドを使用します。  
  
 一般的な場所から同じ例外をスローします。 コードの肥大化を回避するのには、例外を作成し、それらのプロパティを初期化するヘルパー メソッドを使用します。  
  
 また、例外をスローするメンバーが取得されないインライン展開されます。 Throw ステートメント ビルダー内を移動すると、インライン展開を解除するメンバーことができます。  
  
 **X しないで**例外フィルター ブロックから例外をスローします。  
  
 例外フィルターには、例外が発生したときに、CLR で例外をキャッチし、フィルターが false を返します。 この動作を実行して、明示的に false を返すフィルターから区別することであり、デバッグが非常に困難であるためです。  
  
 **避け x**明示的に finally ブロックからの例外をスローします。 暗黙的にスローされたによってスローされる例外をスローするメソッドを呼び出すことは可能です。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [例外のデザインのガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
