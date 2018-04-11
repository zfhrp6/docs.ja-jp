---
title: イベントのデザイン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a07392ba805b5f2a3913b01a15dd0e1668f0ccf7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="event-design"></a>イベントのデザイン
イベントは、コールバック (ユーザー コードを呼び出すために、フレームワークを許可するコンストラクト) の最も一般的に使用される形式です。 その他のコールバック機構には、デリゲート、仮想メンバー、およびプラグインのインターフェイス ベースを取得するメンバーが含まれます。ユーザビリティ調査においてからのデータは、開発者の大部分が快適他のコールバック機構を使用するよりもイベントを使用することを示します。 イベントは、Visual Studio および多くの言語に適切に統合されています。  
  
 イベントの 2 つのグループがあることを確認することが重要: 前のイベント、および状態が変更した後に発生するイベントと呼ばれる、システムの変更の状態の前に発生したイベントには後のイベントが呼び出されます。 イベントの前の例としては`Form.Closing`フォームが閉じる前に、これが発生します。 後のイベントの例としては`Form.Closed`フォームが閉じられた後、これが発生します。  
  
 **✓ しないで**イベントではなく「"発生させる」や「トリガー」の「生成」という用語を使用  
  
 **✓ しないで**使用<xref:System.EventHandler%601?displayProperty=nameWithType>イベント ハンドラーとして使用する新しいデリゲートを手動で作成する代わりにします。  
  
 **✓ を検討してください**のサブクラスを使用して<xref:System.EventArgs>イベントの引数としてイベントをイベント メソッドを処理するデータを実行する必要はありませんが確実でない限り、その場合は行うこともできます、`EventArgs`を直接入力します。  
  
 API を使用して、出荷する場合`EventArgs`直接、しないことができますを互換性の問題なしイベントに実行されるようにデータを追加します。 サブクラスを使用する場合でもかどうか、最初に完全に空ことができます必要なときに、サブクラスにプロパティを追加します。  
  
 **✓ しないで**各イベントを生成するプロテクト仮想メソッドを使用します。 これは構造体、シール クラス、または静的イベントが、封印されていないクラスで静的でないイベントに適用します。  
  
 メソッドの目的は、上書きを使用して、イベントを処理する派生クラスの手段を提供します。 オーバーライドは、派生クラスで基底クラスのイベントを処理するより柔軟で、高速より自然な方法です。 規則では、メソッドの名前が"On"で開始する必要があり、イベントの名前の後にします。  
  
 派生クラスは、そのオーバーライドで、メソッドの基本実装を呼び出していないを選択できます。 正常に動作する基本クラスに必要なメソッドでなんらかの処理を含めないことでこれを準備します。  
  
 **✓ しないで**イベントを発生させる保護されたメソッドを 1 つのパラメーターを取得します。  
  
 パラメーターの名前が付けられます`e`と、イベント引数クラスとして自動的に入力する必要があります。  
  
 **X しないで**静的でないイベントを発生させる場合するセンダとして null を渡します。  
  
 **✓ しないで**静的イベントを発生させる場合するセンダとして null を渡します。  
  
 **X しないで**イベントを発生させるときにイベント データ パラメーターとして null を渡します。  
  
 渡す必要があります`EventArgs.Empty`イベント処理メソッドに、データの受け渡ししたくない場合。 開発者は、いない null にするには、このパラメーターを必要とします。  
  
 **✓ を検討してください**エンドユーザーが取り消すことができるイベントを発生させます。 これは、前のイベントにのみ適用されます。  
  
 使用して<xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>またはエンドユーザーのイベントをキャンセルできるイベントの引数としてそのサブクラスです。  
  
### <a name="custom-event-handler-design"></a>カスタム イベント ハンドラーのデザイン  
 場合がある`EventHandler<T>`フレームワークが、ジェネリックをサポートしていませんでしたが、CLR の以前のバージョンを使用する必要がある場合など、使用することはできません。 このような場合は、デザインおよびカスタム イベント ハンドラーのデリゲートを作成する必要があります。  
  
 **✓ しないで**イベント ハンドラーの void の戻り値の型を使用します。  
  
 イベント ハンドラーは、可能性のある複数のオブジェクトのメソッドを処理する複数のイベントを呼び出すことができます。 イベント処理メソッドの戻り値が許可された場合は、各イベントの呼び出しに複数の戻り値があります。  
  
 **✓ は**を使用して`object`イベント ハンドラーの最初のパラメーターの型としてそれを呼び出すと`sender`です。  
  
 **✓ しないで**を使用して<xref:System.EventArgs?displayProperty=nameWithType>またはそのサブクラスをイベント ハンドラーの 2 番目のパラメーターの型としてそれを呼び出すと`e`です。  
  
 **X しないで**イベント ハンドラーに次の 2 つ以上のパラメーターがあります。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
