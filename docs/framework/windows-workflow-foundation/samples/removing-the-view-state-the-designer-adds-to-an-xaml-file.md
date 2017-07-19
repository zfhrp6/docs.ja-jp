---
title: "デザイナーによって XAML ファイルに追加されるビューステートの削除 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# デザイナーによって XAML ファイルに追加されるビューステートの削除
このサンプルでは、<xref:System.Windows.Markup.XamlWriter> から派生するクラスを作成する方法を示し、XAML ファイルからビューステートを削除します。[!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] は、ビューステートと呼ばれる情報を XAML ドキュメントに書き込みます。ビューステートは、ランタイムでは不必要なレイアウト配置などの、デザイン時に必要な情報を参照します。[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] は、編集時に、XAML ドキュメントにこの情報を挿入します。[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] は、`mc:Ignorable` 属性を持つ XAML ファイルにビュー ステートを書き込みます。この結果、ランタイムが XAML ファイルを読み込みとき、この情報は読み込まれません。このサンプルでは、XAML ノードの処理中にそのビューステート情報を削除するクラスを作成する方法を示します。  
  
## 説明  
 このサンプルでは、カスタム ライターを作成する方法を示します。  
  
 カスタム XAML ライターをビルドするには、<xref:System.Windows.Markup.XamlWriter> を継承するクラスを作成します。XAML ライターは入れ子になっていることが多いので、通常は "内部" XAML ライターを追跡します。この "内部" ライターは XAML ライターの残りのスタックへの参照と考えることができ、これによって複数のエントリ ポイントで処理が実行されるようにし、処理を残りのスタックにデリゲートすることができます。  
  
 このサンプルには、重要な項目がいくつかあります。その 1 つとして、書き込まれる項目がデザイナー名前空間からのものであるかどうかの確認が挙げられます。これにより、ワークフローでデザイナー名前空間の他の型の使用が排除されることに注意してください。  
  
```  
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)  
{  
return xamlMember.IsAttachable &&  
   xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);  
}  
  
const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";  
The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.  
public ViewStateCleaningWriter(XamlWriter innerWriter)  
{  
this.InnerWriter = innerWriter;  
this.MemberStack = new Stack<XamlMember>();  
}  
  
XamlWriter InnerWriter {get; set; }  
Stack<XamlMember> MemberStack {get; set; }  
  
```  
  
 これにより、ノード ストリームの走査中に使用される XAML メンバーのスタックも作成されます。このサンプルの残りの作業は、主に <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A> メソッドに含まれています。  
  
```  
public override void WriteStartMember(XamlMember xamlMember)  
{  
MemberStack.Push(xamlMember);  
if (IsDesignerAttachedProperty(xamlMember))  
{  
m_attachedPropertyDepth++;  
}  
  
if (m_attachedPropertyDepth > 0)  
{  
return;  
}  
  
InnerWriter.WriteStartMember(xamlMember);  
}  
  
```  
  
 後続のメソッドで、まだビューステート コンテナーに含まれているかどうかがチェックされ、含まれている場合は制御が戻り、ノードはライター スタックに渡されません。  
  
```  
public override void WriteValue(Object value)  
{  
if (m_attachedPropertyDepth > 0)  
{  
return;  
}  
  
InnerWriter.WriteValue(value);  
}  
```  
  
 カスタム XAML ライターを使用するには、XAML ライターのスタックでまとめて連結する必要があります。この使用方法を次のコードに示します。  
  
```  
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
  
```  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ViewStateCleaningWriter.sln ソリューション ファイルを開きます。  
  
2.  コマンド プロンプトを開き、ViewStageCleaningWriter.exe がビルドされているディレクトリに移動します。  
  
3.  Workflow1.xaml ファイルに対して ViewStateCleaningWriter.exe を実行します。  
  
     実行可能ファイルの構文の例を次に示します。  
  
 **ViewStateCleaningWriter.exe \[入力ファイル\] \[出力ファイル\]**     これにより、XAML ファイルは、すべてのビューステート情報が削除された状態で \[出力ファイル\] に出力されます。  
  
    > [!NOTE]
    >  <xref:System.Activities.Statements.Sequence> ワークフローでは、多数の仮想化のヒントが削除されます。その結果、デザイナーは次回の読み込み時にレイアウトを再計算します。このサンプルを <xref:System.Activities.Statements.Flowchart> に対して使用すると、すべての配置情報および線のルーティング情報が削除され、後続のデザイナーへの読み込み時にすべてのアクティビティが画面の左側に積み上げられます。  
  
#### このサンプルで使用するサンプル XAML ファイルを作成するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を開きます。  
  
2.  新しいワークフロー コンソール アプリケーションを作成します。  
  
3.  いくつかのアクティビティをキャンバスにドラッグ アンド ドロップします。  
  
4.  ワークフロー XAML ファイルを保存します。  
  
5.  XAML ファイルを調べて、ビューステートの添付プロパティを確認します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`  
  
## 参照