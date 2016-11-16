---
title: "弱い参照"
description: "弱い参照"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/19/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 22319f2f-0008-4ace-815e-545892a0512a
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: cc43c319f2ec8055073da4749cbfb7c56b825df9

---

# <a name="weak-references"></a>弱い参照

ガベージ コレクターでは、アプリケーションのコードがオブジェクトにアクセスできる間、そのアプリケーションで使用中のオブジェクトを収集することはできません。 アプリケーションには、オブジェクトへの強い参照があると考えられます。 

弱い参照は、アプリケーションからオブジェクトへのアクセスを許容したまま、そのオブジェクトをガベージ コレクターが収集できるようにします。 弱い参照は、強い参照が存在しない場合に、オブジェクトが収集されるまでの不確定の期間中のみ有効です。 弱い参照を使用すると、該当オブジェクトが収集されるのを回避するため、アプリケーションで強い参照を取得できます。 ただし、強い参照が再確立される前に、ガベージ コレクターが最初にオブジェクトにアクセスするリスクが常にあります。

弱い参照は、多くのメモリを使用するが、ガベージ コレクションによって回収される場合、簡単に再作成できるオブジェクトに便利です。 

ツリー ビューに、複雑な階層形式のオプション選択がユーザーに示されているとします。 基になるデータが大きければ、ユーザーがアプリケーションで他の操作を行っている場合、ツリーをメモリ内に保持しても効果的ではありません。 

ユーザーがアプリケーションの別の部分に切り替えている場合、[WeakReference](xref:System.WeakReference) または [WeakReference&lt;T&gt;](xref:System.WeakReference%601) クラスを使用して、ツリーへの弱い参照を作成し、すべての強い参照を破棄できます。 ユーザーがツリーに戻ると、アプリケーションはツリーへの強い参照を取得しようとします。成功した場合、ツリーの再作成は回避されます。

オブジェクトで弱い参照を確立するには、追跡されるオブジェクトのインスタンスを使用して、[WeakReference](xref:System.WeakReference) を作成します。 次に、そのオブジェクトの [Target](xref:System.WeakReference.Target) プロパティを設定して、オブジェクトへの元の参照を null に設定します。 

## <a name="short-and-long-weak-references"></a>短期間と長期間の弱い参照

短期間の弱い参照または長期間の弱い参照を作成できます。 

* Short

  短期間の弱い参照の対象は、オブジェクトがガベージ コレクションによって回収されると、`null` になります。 弱い参照自体が管理オブジェクトであり、その他の管理オブジェクトと同じようにガベージ コレクションの対象です。 短期間の弱い参照は、[WeakReference](xref:System.WeakReference) の既定のコンス トラクターです。 

* Long

  長期間の弱い参照は、オブジェクトの [Finalize](xref:System.Object.Finalize) メソッドが呼び出された後も保持されます。 これにより、オブジェクトが再作成されることを許可しますが、オブジェクトの状態は予測不可能なままです。 長い参照を使用するには、[WeakReference](xref:System.WeakReference) コンストラクターに `true` を指定します。 

  オブジェクトの型に [Finalize](xref:System.Object.Finalize) メソッドがない場合、短期間の弱い参照の機能が適用され、弱い参照はターゲットが収集されるまで有効です。これはファイナライザーを実行した後であれば、いつでも発生する可能性があります。

強い参照を確立して、もう一度オブジェクトを使用するには、オブジェクトの型に [WeakReference](xref:System.WeakReference) の [Target](xref:System.WeakReference.Target) プロパティをキャストします。 [Target](xref:System.WeakReference.Target) プロパティが `null` を返す場合、オブジェクトが収集されます。それ以外の場合、アプリケーションがその強い参照を再取得するため、オブジェクトを使用し続けることができます。

## <a name="guidelines-for-using-weak-references"></a>弱い参照を使用するためのガイドライン

終了処理後のオブジェクトの状態が予測できないため、長期間の弱い参照は必要な場合にのみ使用します。 

ポインター自体が同程度の大きさか、より大きい場合があるため、小さなオブジェクトへの弱い参照を使用しないでください。 

メモリ管理の問題への自動的な解決方法として、弱い参照を使用しないでください。 代わりに、アプリケーションのオブジェクトを処理するために、効果的なキャッシュ ポリシーを開発します。 

## <a name="see-also"></a>関連項目

[.NET のガベージ コレクション](index.md)



<!--HONumber=Nov16_HO1-->


