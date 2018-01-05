---
title: "コレクションに関するガイドライン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 62205e6bea39214383f6a653d719c0285f374a9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="guidelines-for-collections"></a>コレクションに関するガイドライン
任意の型が共通の特性を持つオブジェクトのグループの操作を厳密には、コレクションを見なすことができます。 実装するには、このような型に適したはほぼ<xref:System.Collections.IEnumerable>または<xref:System.Collections.Generic.IEnumerable%601>、このセクションの内容おのみ考慮されるようにコレクションにそれらのインターフェイスの一方または両方を実装する型。  
  
 **X しないで**パブリック Api で弱く型指定されたコレクションを使用します。  
  
 すべての戻り値およびパラメーターを表すコレクション アイテムの種類は、その基本型 (これは、コレクションのパブリック メンバーにのみ適用) の正確な項目の種類にする必要があります。  
  
 **X しないで**使用<xref:System.Collections.ArrayList>または<xref:System.Collections.Generic.List%601>パブリック Api でします。  
  
 これらの型は、パブリック Api ではなく、内部の実装で使用するためのデータ構造です。 `List<T>`パフォーマンスと電力消費 cleanness Api と柔軟性を犠牲に最適です。 返す場合など、 `List<T>`、いない続けることができますをクライアント コードは、コレクションを変更するときに通知を受信します。 また、`List<T>`など多くのメンバーを公開<xref:System.Collections.Generic.List%601.BinarySearch%2A>、いないの役に立たず、多くのシナリオに該当します。 次の 2 つのセクションでは、パブリック Api で使用する専用に設計された型 (抽象) について説明します。  
  
 **X しないで**使用`Hashtable`または`Dictionary<TKey,TValue>`パブリック Api でします。  
  
 これらの型は、データ構造体の内部実装に使用するよう設計されています。 パブリック Api を使用する必要があります<xref:System.Collections.IDictionary>、 `IDictionary <TKey, TValue>`、またはいずれかまたは両方のインターフェイスを実装するカスタム型です。  
  
 **X しないで**使用<xref:System.Collections.Generic.IEnumerator%601>、 <xref:System.Collections.IEnumerator>、またはその他の型以外の戻り値の型として実装する、これらのインターフェイスのいずれかを`GetEnumerator`メソッドです。  
  
 以外の場合、メソッドから列挙子を返す型`GetEnumerator`では使用できません、`foreach`ステートメントです。  
  
 **X しないで**両方を実装する`IEnumerator<T>`と`IEnumerable<T>`と同じ型にします。 非ジェネリック インターフェイスに適用される同じ`IEnumerator`と`IEnumerable`です。  
  
## <a name="collection-parameters"></a>コレクションのパラメーター  
 **✓ しないで**パラメーター型として型の最小に特化した可能性のあるを使用します。 ほとんどのメンバーを使用するパラメーターとして、コレクションを受け取る、`IEnumerable<T>`インターフェイスです。  
  
 **避け x**を使用して<xref:System.Collections.Generic.ICollection%601>または<xref:System.Collections.ICollection>にアクセスするだけのパラメーターとして、`Count`プロパティです。  
  
 代わりに、`IEnumerable<T>`または`IEnumerable`と動的にオブジェクトが実装されているかどうかをチェック`ICollection<T>`または`ICollection`です。  
  
## <a name="collection-properties-and-return-values"></a>コレクションのプロパティと戻り値  
 **X しないで**設定可能なコレクション プロパティを提供します。  
  
 ユーザーは、最初、コレクションをクリアして、新しい内容を追加し、コレクションの内容を置き換えることができます。 コレクション全体を置き換えることがある場合、一般的なシナリオを提供することを検討してください、`AddRange`コレクション メソッド。  
  
 **✓ は**を使用して`Collection<T>`またはそのサブクラスの`Collection<T>`プロパティまたは戻り値を表す読み取り/書き込みコレクション用です。  
  
 場合`Collection<T>`いくつかの条件を満たしていません (など、コレクションを実装する必要がありますいない<xref:System.Collections.IList>)、実装することによってカスタム コレクションを使用して`IEnumerable<T>`、 `ICollection<T>`、または<xref:System.Collections.Generic.IList%601>です。  
  
 **✓ は**使用<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>のサブクラス`ReadOnlyCollection<T>`、まれなケースとして、または`IEnumerable<T>`プロパティまたは戻り値を表す読み取り専用のコレクションのです。  
  
 一般に、必要に応じて`ReadOnlyCollection<T>`です。 いくつかの要件を満たしていない場合 (など、コレクションを実装する必要がありますいない`IList`)、実装することによってカスタム コレクションを使用して`IEnumerable<T>`、 `ICollection<T>`、または`IList<T>`です。 カスタムの読み取り専用コレクションを実装する場合は、実装`ICollection<T>.ReadOnly`false を返します。  
  
 あるか、唯一のシナリオをサポートすることがイテレーションを順方向専用であることを確認する場合、単に使用できます`IEnumerable<T>`です。  
  
 **✓ を検討してください**ジェネリックの基本コレクションのサブクラスを使用して、コレクションを直接使用する代わりにします。  
  
 これにより、名前を向上し、基本コレクション型に記載されていないヘルパー メンバーを追加するためです。 これは、特に高水準の Api を適用します。  
  
 **✓ を検討してください**のサブクラスを返す`Collection<T>`または`ReadOnlyCollection<T>`から非常に一般的に使用されるメソッドとプロパティ。  
  
 これが可能になりますヘルパー メソッドを追加またはコレクション実装では、今後の変更を行うためです。  
  
 **✓ を検討してください**コレクションに格納されている項目が一意キーを持つ場合、キー付きコレクションを使用する (名前、Id などです。)。 キー付きコレクションは、整数値とキーの両方でインデックスを作成できる通常を継承して実装するコレクション`KeyedCollection<TKey,TItem>`です。  
  
 キー付きコレクション通常より大きなメモリ フット プリントとには、メモリのオーバーヘッドが、キーの利点を上回る場合、使用できません。  
  
 **X しないで**コレクション プロパティまたはコレクションを返すメソッドから null 値を返します。 代わりに、空のコレクションまたは空の配列を返します。  
  
 一般的な規則は、null および空の (0 項目) のコレクションまたは配列をする必要があります同じ扱われます。  
  
### <a name="snapshots-versus-live-collections"></a>ライブのコレクションとの比較のスナップショット  
 時刻である時点の状態を表すコレクションは、スナップショットのコレクションと呼ばれます。 たとえば、データベース クエリから返される行を含むコレクションのスナップショットがあります。 常に現在の状態を表すコレクションは、ライブのコレクションと呼ばれます。 たとえば、一連の`ComboBox`項目はライブのコレクション。  
  
 **X しないで**プロパティからスナップショットのコレクションを返します。 プロパティは、ライブのコレクションを返す必要があります。  
  
 プロパティ get アクセス操作子は、非常に軽量の操作をする必要があります。 スナップショットを取得するには、o (n) 操作の内部コレクションのコピーを作成する必要があります。  
  
 **✓ しないで**スナップショット コレクションまたはライブのいずれかを使用して`IEnumerable<T>`(またはそのサブタイプ) は揮発性であるコレクションを表現する (つまり、変更可能なコレクションを明示的に変更することがなく)。  
  
 一般に、共有リソース (ディレクトリ内のファイルなど) を表すすべてのコレクションは、揮発性です。 このようなコレクションは、非常に困難か不可能実装が単に、順方向専用の列挙子でない限り、ライブのコレクションとして実装するにです。  
  
## <a name="choosing-between-arrays-and-collections"></a>配列またはコレクションの選択  
 **✓ しないで**コレクションを配列よりも優先されます。  
  
 コレクションは、時間の経過とともに進化させることができます、およびがより使いやすくする内容より詳細に制御を提供します。 さらに、読み取り専用の配列の使用はお勧め、配列の複製のコストが非常に大きいためです。 使いやすさの調査によると、一部の開発者と感じるユーザー コレクション ベースの Api を使用します。  
  
 ただし、低レベルの Api を開発している場合、読み取り/書き込みのシナリオの配列を使用する方がよい場合があります。 配列は、メモリの使用量、ワーキング セットを削減できるようにするには、これを持ち、ランタイムによって、最適化されているために、配列内の要素へのアクセスが高速化。  
  
 **✓ を検討してください**低レベルの Api でのメモリ消費量を最小限に抑えるし、パフォーマンスを最大化する配列を使用します。  
  
 **✓ しないで**バイトのコレクションではなくバイト配列を使用します。  
  
 **X しないで**プロパティをプロパティ getter を呼び出すたびに新しい配列 (内部の配列のコピーなど) を返す必要がある場合、プロパティの配列を使用します。  
  
## <a name="implementing-custom-collections"></a>カスタム コレクションを実装します。  
 **✓ を検討してください**から継承する`Collection<T>`、 `ReadOnlyCollection<T>`、または`KeyedCollection<TKey,TItem>`新しいコレクションを設計するとき。  
  
 **✓ しないで**実装`IEnumerable<T>`新しいコレクションを設計するとき。 実装の検討`ICollection<T>`またはでも`IList<T>`理にかなっています。  
  
 このようなカスタム コレクションを実装するには場合、によって確立された API のパターンに従う`Collection<T>`と`ReadOnlyCollection<T>`可能な限りです。 つまり、同じメンバーを明示的に実装する、これら 2 つのコレクションに名前を付けてなどと同様に、パラメーターの名前を付けます。  
  
 **✓ を検討してください**非ジェネリック コレクション インターフェイスを実装する (`IList`と`ICollection`) 場合は、コレクションは多くの場合する Api に渡される入力としてこれらのインターフェイスを取得します。  
  
 **避け x**コレクションの概念とは無関係な複雑な Api を使用した型にコレクション インターフェイスを実装します。  
  
 **X しないで**など非ジェネリックの基本コレクションから継承`CollectionBase`です。 使用して`Collection<T>`、 `ReadOnlyCollection<T>`、および`KeyedCollection<TKey,TItem>`代わりにします。  
  
### <a name="naming-custom-collections"></a>名前付けのカスタム コレクション  
 コレクション (型を実装する`IEnumerable`) 主に 2 つの理由が作成されますパフォーマンス特性が異なる既存のデータ構造体と構造体に固有の操作と多くの場合は、新しいデータ構造を作成するには、(1) (例: <xref:System.Collections.Generic.List%601>、。<xref:System.Collections.Generic.LinkedList%601>、 <xref:System.Collections.Generic.Stack%601>)、および特定の項目のセットを保持するための特殊化されたコレクションを作成するには、(2) (例: <xref:System.Collections.Specialized.StringCollection>)。 データ構造体は、アプリケーションおよびライブラリの内部的な実装で最もよく使用されます。 専用コレクションは、(プロパティおよびパラメーターの型) として Api で公開するには、主に、します。  
  
 **✓ しないで**を実装する抽象クラスの名前に「ディクショナリ」サフィックスを使用`IDictionary`または`IDictionary<TKey,TValue>`です。  
  
 **✓ しないで**を実装する型の名前に「コレクション」サフィックスを使用`IEnumerable`(またはその子孫のいずれかの) 項目のリストを表すとします。  
  
 **✓ しないで**カスタム データ構造に対する、適切なデータ構造の名前を使用します。  
  
 **避け x**コレクションの抽象化の名前に"LinkedList"または「ハッシュ テーブル、」などの特定の実装の暗黙的な任意のサフィックスを使用します。  
  
 **✓ を検討してください**項目の種類の名前を持つコレクションの名前を付けることです。 たとえば、型の項目を格納するコレクション`Address`(実装`IEnumerable<Address>`) という名前を付ける必要があります`AddressCollection`です。 プレフィックス"I"、項目の種類がインターフェイスの場合は、項目の種類を省略できます。 したがって、一連の<xref:System.IDisposable>項目を呼び出すことができる`DisposableCollection`です。  
  
 **✓ を検討してください**対応する書き込み可能なコレクションが追加されるか、フレームワークに既に存在する場合に、読み取り専用コレクションの名前に"ReadOnly"プレフィックスを使用します。  
  
 たとえば、文字列の読み取り専用コレクションを呼び出す必要があります`ReadOnlyStringCollection`です。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>参照  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
