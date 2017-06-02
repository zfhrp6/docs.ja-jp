---
title: "方法 : TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ListItem"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "例 [Windows フォーム], ListView コントロール"
  - "例 [Windows フォーム], TreeView コントロール"
  - "ListView コントロール [Windows フォーム], 追加 (カスタム情報を)"
  - "Tag プロパティ"
  - "TreeView コントロール [Windows フォーム], 追加 (カスタム情報を)"
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する
Windows フォームの <xref:System.Windows.Forms.TreeView> コントロールに派生ノードを作成したり、<xref:System.Windows.Forms.ListView> コントロールに派生アイテムを作成したりできます。  派生によって、必要な任意のフィールドを追加できます。また、追加するフィールドを操作するための、カスタム メソッドやカスタム コンストラクターを追加することもできます。  この機能の用途の 1 つに、各ツリー ノードまたはリスト項目への Customer オブジェクトの割り当てがあります。  ここでは <xref:System.Windows.Forms.TreeView> コントロールでの例を示しますが、<xref:System.Windows.Forms.ListView> コントロールの場合も同様に操作できます。  
  
### ツリー ノードを派生させるには  
  
-   <xref:System.Windows.Forms.TreeNode> クラスから派生を行って、ファイル パスを記録するためのカスタム フィールドを持つノード クラスを新規作成します。  
  
    ```vb  
    Class myTreeNode  
       Inherits TreeNode  
  
       Public FilePath As String  
  
       Sub New(ByVal fp As String)  
          MyBase.New()  
          FilePath = fp  
          Me.Text = fp.Substring(fp.LastIndexOf("\"))  
       End Sub  
    End Class  
  
    ```  
  
    ```csharp  
    class myTreeNode : TreeNode  
    {  
       public string FilePath;  
  
       public myTreeNode(string fp)  
       {  
          FilePath = fp;  
          this.Text = fp.Substring(fp.LastIndexOf("\\"));  
       }  
    }  
  
    ```  
  
    ```cpp  
    ref class myTreeNode : public TreeNode  
    {  
    public:  
       System::String ^ FilePath;  
  
       myTreeNode(System::String ^ fp)  
       {  
          FilePath = fp;  
          this->Text = fp->Substring(fp->LastIndexOf("\\"));  
       }  
    };  
    ```  
  
### 派生されたツリー ノードを使用するには  
  
1.  新しい派生ツリー ノードは、呼び出した関数に渡すパラメーターとして使用できます。  
  
     次の例では、テキスト ファイルの場所に対するパスとして My Documents フォルダーが設定されています。  これは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、ユーザーは最小限のシステム アクセス レベルでアプリケーションを安全に実行できます。  
  
    ```vb  
    ' You should replace the bold text file   
    ' in the sample below with a text file of your own choosing.  
    TreeView1.Nodes.Add(New myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\ TextFile.txt ") )  
  
    ```  
  
    ```csharp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    treeView1.Nodes.Add(new myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\TextFile.txt") );  
  
    ```  
  
    ```cpp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    treeView1->Nodes->Add(new myTreeNode(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\TextFile.txt")));  
    ```  
  
2.  渡されたツリー ノードが <xref:System.Windows.Forms.TreeNode> クラスに分類される場合は、派生クラスへのキャストを行う必要があります。  キャストとは、オブジェクトを他の型に明示的に変換することです。  キャストの詳細については、「[Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md)」 \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] の場合\)、「[\(\) 演算子](../Topic/\(\)%20Operator%20\(C%23%20Reference\).md)」 \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] の場合\)、または「[キャスト演算子: \(\)](../../../../amples/snippets/visualbasic/VS_Snippets_Wpf/DocumentStructure/visualbasic/spec_withstructure-xps/_rels/.rels)」 \([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] の場合\) を参照してください。  
  
    ```vb  
    Public Sub TreeView1_AfterSelect(ByVal sender As Object, ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       Dim mynode As myTreeNode  
       mynode = CType(e.node, myTreeNode)  
       MessageBox.Show("Node selected is " & mynode.filepath)  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,  
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       myTreeNode myNode = (myTreeNode)e.Node;  
       MessageBox.Show("Node selected is " + myNode.FilePath);  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          myTreeNode ^ myNode = safe_cast<myTreeNode^>(e->Node);  
          MessageBox::Show(String::Concat("Node selected is ",   
             myNode->FilePath));  
       }  
    ```  
  
## 参照  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)