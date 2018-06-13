---
title: '方法: データ バインディングの動作をカスタマイズする (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: 6ebc50a4a4ed2c91db0dcbcb53d3965757a94f9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364140"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>方法: データ バインディングの動作をカスタマイズする (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、バインディング コレクションにオブジェクトを追加したとき、バインディング コレクションからオブジェクトを削除したとき、またはプロパティ変更が検出されたときに、<xref:System.Data.Services.Client.DataServiceCollection%601> によって呼び出されるカスタム ロジックを指定できます。 このカスタム ロジックとして参照されているメソッドとして提供される<xref:System.Func%602>の値を返すデリゲート`false`ときに既定の動作を引き続き実行するカスタム メソッドの完了時に、`true`後続の処理時に、イベントを停止する必要があります。  
  
 このトピックの例は、`entityChanged` の `entityCollectionChanged` パラメーターと <xref:System.Data.Services.Client.DataServiceCollection%601> パラメーターの両方のカスタム メソッドを示します。 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 完了したときにこのサービスおよびクライアント データ クラスが作成された、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)です。  
  
## <a name="example"></a>例  
 次の XAML ファイルの分離コード ページは、バインディング コレクションにバインドされたデータへの変更が発生すると呼び出される <xref:System.Data.Services.Client.DataServiceCollection%601> とカスタム メソッドを作成します。 <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> イベントが発生すると、指定したメソッドは、バインディング コレクションから削除された項目がデータ サービスから削除されることを防止します。 <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> イベントが発生すると、出荷済みの注文に対する変更がないことを確認するために、`ShipDate` の値が検証されます。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>例  
 次の XAML は、前の例のウィンドウを定義します。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>関連項目  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
