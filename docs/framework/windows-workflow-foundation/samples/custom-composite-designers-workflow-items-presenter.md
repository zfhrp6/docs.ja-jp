---
title: "カスタム複合デザイナー - Workflow Items Presenter | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# カスタム複合デザイナー - Workflow Items Presenter
<xref:System.Activities.Design.WorkflowItemsPresenter> は、格納されている要素のコレクションを編集できる、WF デザイナー プログラミング モデル内の主要な型です。このサンプルでは、このような編集可能なコレクションを表示するアクティビティ デザイナーの構築方法を示します。  
  
 このサンプルでは、次の方法を示します。  
  
-   <xref:System.Activities.Design.WorkflowItemsPresenter> を使用したカスタム アクティビティ デザイナーの作成。  
  
-   "折りたたまれている" および "展開されている" ビューを示すアクティビティ デザイナーの作成  
  
-   再ホストされたアプリケーションでの既定のデザイナーのオーバーライド  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  C\# または VB 用の **UsingWorkflowItemsPresenter.sln** サンプル ソリューションを [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で開きます。  
  
2.  ソリューションをビルドして実行します。再ホストされたワークフロー デザイナー アプリケーションが開き、アクティビティをキャンバスにドラッグできます。  
  
## サンプルの詳細  
 このサンプルのコードには、次の内容が表示されます。  
  
-   デザイナーをビルドするアクティビティは `Parallel` です。  
  
-   <xref:System.Activities.Design.WorkflowItemsPresenter> を使用してカスタム アクティビティ デザイナーを作成します。次の点に注意してください。  
  
    -   `ModelItem.Branches` にバインドする WPF のデータ バインドの使用に注意してください。`ModelItem` は、デザイナーが使用されている、基になるオブジェクト \(この例では `Parallel`\) を参照する <xref:System.Activities.Design.WorkflowElementDesigner> のプロパティです。  
  
    -   <xref:System.Activities.Design.WorkflowItemsPresenter.SpacerTemplate%2A> は、コレクション内の個々の項目間にビジュアル表示を配置するために使用できます。  
  
    -   <xref:System.Activities.Design.WorkflowItemsPresenter.ItemsPanel%2A> は、コレクション内の項目のレイアウトを決定するために提供できるテンプレートです。この例では、水平方向のスタック パネルが使用されます。  
  
 このコード例を次に示します。  
  
```xaml  
<sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                              Items="{Binding Path=ModelItem.Branches}">  
    <sad:WorkflowItemsPresenter.SpacerTemplate>  
      <DataTemplate>  
        <Ellipse Width="10" Height="10" Fill="Black"/>  
      </DataTemplate>  
    </sad:WorkflowItemsPresenter.SpacerTemplate>  
    <sad:WorkflowItemsPresenter.ItemsPanel>  
      <ItemsPanelTemplate>  
        <StackPanel Orientation="Horizontal"/>  
      </ItemsPanelTemplate>  
    </sad:WorkflowItemsPresenter.ItemsPanel>  
  </sad:WorkflowItemsPresenter>  
  
```  
  
-   `DesignerAttribute` の `Parallel` 型への関連付けを実行し、報告された属性を出力します。  
  
    -   最初に、すべての既定のデザイナーを登録します。  
  
 このコード例を次に示します。  
  
```csharp  
// register metadata  
(new DesignerMetadata()).Register();  
RegisterCustomMetadata();  
  
```  
  
```vb  
' register metadata  
Dim metadata = New DesignerMetadata()  
metadata.Register()  
' register custom metadata  
RegisterCustomMetadata()  
  
```  
  
-   -   次に、`RegisterCustomMetadata` メソッドで parallel をオーバーライドします。  
  
 次に、C\# と Visual Basic のコード例をそれぞれ示します。  
  
 C\#  
  
```csharp  
void RegisterCustomMetadata()  
{  
      AttributeTableBuilder builder = new AttributeTableBuilder();  
      builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
      MetadataStore.AddAttributeTable(builder.CreateTable());  
}  
  
```  
  
```vb  
Sub RegisterCustomMetadata()  
   Dim builder As New AttributeTableBuilder()  
   builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))  
   MetadataStore.AddAttributeTable(builder.CreateTable())  
End Sub  
  
```  
  
-   最後に、さまざまなデータ テンプレートとトリガーを使用して、`IsRootDesigner` プロパティに基づいて適切なテンプレートを選択していることに注目してください。  
  
 このコード例を次に示します。  
  
```xaml  
<sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"  
    xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">  
  <sad:ActivityDesigner.Resources>  
    <DataTemplate x:Key="Expanded">  
      <StackPanel>  
        <TextBlock>This is the Expanded View</TextBlock>  
        <sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                    Items="{Binding Path=ModelItem.Branches}">  
          <sad:WorkflowItemsPresenter.SpacerTemplate>  
            <DataTemplate>  
              <Ellipse Width="10" Height="10" Fill="Black"/>  
            </DataTemplate>  
          </sad:WorkflowItemsPresenter.SpacerTemplate>  
          <sad:WorkflowItemsPresenter.ItemsPanel>  
            <ItemsPanelTemplate>  
              <StackPanel Orientation="Horizontal"/>  
            </ItemsPanelTemplate>  
          </sad:WorkflowItemsPresenter.ItemsPanel>  
        </sad:WorkflowItemsPresenter>  
      </StackPanel>  
    </DataTemplate>  
    <DataTemplate x:Key="Collapsed">  
      <TextBlock>This is the Collapsed View</TextBlock>  
    </DataTemplate>  
    <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
      <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
      <Style.Triggers>  
        <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">  
          <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
        </DataTrigger>  
      </Style.Triggers>  
    </Style>  
  </sad: ActivityDesigner.Resources>  
  <Grid>  
    <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
  </Grid>  
</sad: ActivityDesigner>  
  
```  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## 参照  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>   
 [ワークフロー デザイナーを使用したアプリケーションの開発](../Topic/Developing%20Applications%20with%20the%20Workflow%20Designer.md)