---
title: オプティミスティック同時実行の概要
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: 5b4603526896364285cb3c85d12568ed9031ed47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362929"
---
# <a name="optimistic-concurrency-overview"></a>オプティミスティック同時実行の概要
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] はオプティミスティック同時実行制御をサポートします。 次の表でオプティミスティック同時実行制御を適用する条件[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ドキュメント。  
  
|用語|説明|  
|-----------|-----------------|  
|同時実行|2 人以上のユーザーがデータベースの同じ行を同時に更新しようとした状況のことです。|  
|同時実行の競合|2 人以上のユーザーが、行の中の 1 つまたは複数の列に対し、互いに競合する値を送信しようとした状況のことです。|  
|同時実行制御|同時実行の競合を解決するために使用する手法のことです。|  
|オプティミスティック同時実行制御|他のトランザクションが行の値に変更を加えていないかどうかをまず調べたうえで変更の送信を許可する手法のことです。<br /><br /> 比較して*ペシミスティック同時実行制御*、同時実行の競合を回避するレコードをロックします。<br /><br /> *オプティミスティック*干渉別の可能性がありますいないを 1 つのトランザクションになる可能性と見なされるために、コントロールはこれと呼ばれます。|  
|競合の解決|データベースを再度クエリしてから相違点を調整することによって競合する項目を更新する処理のことです。<br /><br /> オブジェクトを更新するときには、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の変更トラッカーによって、以下のデータが記録されます。<br /><br /> 最初に、データベースから取得および更新プログラムの使用-の値を確認します。<br />-データベースから新しい値後続のクエリ。<br /><br /> 次に [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、オブジェクトが競合しているかどうか (つまり 1 つまたは複数のメンバー値が変更されているかどうか) を判断します。 オブジェクトが競合している場合[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]次に競合がどのメンバーを決定します。<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] が見つけたメンバーの競合は、競合の一覧に追加されます。|  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデル、*オプティミスティック同時実行の競合*の両方の次の条件に当てはまるときに発生します。  
  
-   クライアントがデータベースに変更を送信しようとした。  
  
-   データベースで、そのクライアントによる最後の読み取り以降に、1 つまたは複数の更新チェック値が更新されている。  
  
 この競合を解決するためには、オブジェクトのどのメンバーが競合しているかを判別し、どのように対処するかを決定することが必要です。  
  
> [!NOTE]
>  オプティミスティック同時実行のチェックに関与するのは、<xref:System.Data.Linq.Mapping.UpdateCheck.Always> または <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> として割り当てられているメンバーのみです。 <xref:System.Data.Linq.Mapping.UpdateCheck.Never> と指定されているメンバーには、チェックは実行されません。 詳細については、「<xref:System.Data.Linq.Mapping.UpdateCheck>」を参照してください。  
  
## <a name="example"></a>例  
 次のシナリオは、ユーザー 1 が、更新の手始めとして、データベースの行をクエリした状況です。 ユーザー 1 が取得した行には、Alfreds、Maria、および Sales という値が入っています。  
  
 ユーザー 1 は、Manager 列の値を Alfred に、また Department 列の値を Marketing に、それぞれ変更しようと考えています。 しかし、ユーザー 1 がその変更を発行する前に、ユーザー 2 がデータベースに変更を送信しました。 その結果、Assistant 列の値は Mary に、また Department 列の値は Service に、それぞれ変更されました。  
  
 ここで、ユーザー 1 が変更を送信しようとすると、送信は失敗し、<xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。 このような結果になるのは、データベースの Assistant 列と Department 列の値が、予期した値と異なるためです。 Assistant 列と Department 列を表すメンバーが競合しています。 この状況をまとめると次の表のようになります。  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|元の状態|Alfreds|Maria|Sales|  
|ユーザー 1|Alfred||Marketing|  
|ユーザー 2||Mary|サービス|  
  
 このような競合は、いくつかの方法で解決できます。 詳細については、次を参照してください。[する方法: 変更の競合を管理](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)です。  
  
## <a name="conflict-detection-and-resolution-checklist"></a>競合の検出と解決のチェック リスト  
 競合の検出と解決は、さまざまな詳細レベルで行うことができます。 極端な方法としては、すべての競合を 3 つの方法 (<xref:System.Data.Linq.RefreshMode> を参照) のいずれかで 1 つで解決し、それ以外の考慮を一切加えないという方法もあります。 正反対の方法としては、競合している各メンバーについて、それぞれの競合の種類ごとに、特定の処理を指定するという方法もあります。  
  
-   オブジェクト モデルの <xref:System.Data.Linq.Mapping.UpdateCheck> オプションを指定または変更します。  
  
     詳細については、次を参照してください。[する方法: 同時実行の競合があるテストを指定するメンバー](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)です。  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A> の呼び出しの try/catch ブロックで、例外がどの時点でスローされるかを指定します。  
  
     詳細については、次を参照してください。[する方法: 指定のときに同時実行例外がスローされた](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)です。  
  
-   取得する競合の詳細さを判断し、それに応じたコードを try/catch ブロックに記述します。  
  
     詳細については、次を参照してください。[する方法: エンティティの競合情報の取得](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)と[する方法: メンバーの競合情報の取得](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)です。  
  
-   含める、 `try` / `catch`を探索するさまざまな競合を解決する方法のコードします。  
  
     詳細については、次を参照してください[する方法: データベースの値を保持して競合の解決](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)、[する方法: データベースの値を上書きして競合の解決](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)、および[する方法: マージ競合を解決するには。データベースの値を持つ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)します。  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>競合の発見と解決をサポートする LINQ to SQL の型  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で、オプティミスティック同時実行の競合の解決をサポートするクラスと機能を以下に示します。  
  
-   <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>関連項目  
 [方法 : 変更の競合を管理する](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
