---
title: '方法 : TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
ms.openlocfilehash: b4131504e5c5d7f2075c72c72b98153c783000d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527418"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="eea3d-102">方法 : TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="eea3d-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="eea3d-103">派生ノードを作成するには、Windows フォームで<xref:System.Windows.Forms.TreeView>コントロールまたはの item の派生、<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="eea3d-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="eea3d-104">派生により、必要なフィールドだけではなく、それらを処理するためのカスタム メソッドやコンストラクターも追加できます。</span><span class="sxs-lookup"><span data-stu-id="eea3d-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="eea3d-105">この機能を使用して、顧客オブジェクトを各ツリー ノードや各リスト項目にアタッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="eea3d-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="eea3d-106">例をここでは、<xref:System.Windows.Forms.TreeView>のコントロールですが、これと同じアプローチを使用できます、<xref:System.Windows.Forms.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="eea3d-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="eea3d-107">ツリー ノードを派生するには</span><span class="sxs-lookup"><span data-stu-id="eea3d-107">To derive a tree node</span></span>  
  
-   <span data-ttu-id="eea3d-108">派生する新しいノード クラスを作成、<xref:System.Windows.Forms.TreeNode>クラスで、ファイルのパスを記録するカスタム フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="eea3d-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="eea3d-109">派生されたツリー ノードを使用するには</span><span class="sxs-lookup"><span data-stu-id="eea3d-109">To use a derived tree node</span></span>  
  
1.  <span data-ttu-id="eea3d-110">新たに派生されたツリー ノードは、関数呼び出しに対するパラメーターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="eea3d-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="eea3d-111">次の例では、テキスト ファイルの場所に設定されているパスは My Documents フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="eea3d-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="eea3d-112">このように設定できるのは、Windows オペレーティング システムを実行しているほとんどのコンピューターにこのディレクトリが含まれていると想定できるからです。</span><span class="sxs-lookup"><span data-stu-id="eea3d-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="eea3d-113">また、このようにすることで、最小限のシステム アクセス レベルしか持たないユーザーもアプリケーションを安全に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="eea3d-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
  
2.  <span data-ttu-id="eea3d-114">ツリー ノードが渡されとして入力したかどうか、<xref:System.Windows.Forms.TreeNode>クラス、派生クラスにキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eea3d-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="eea3d-115">キャストとは、ある型のオブジェクトから別の型のオブジェクトに明示的に変換することです。</span><span class="sxs-lookup"><span data-stu-id="eea3d-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="eea3d-116">キャストの詳細については、次を参照してください。[暗黙的および明示的な変換](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)(Visual Basic)、 [() 演算子](~/docs/csharp/language-reference/operators/invocation-operator.md)(Visual C# の場合)、または[キャスト演算子: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="eea3d-116">For more information on casting, see [Implicit and Explicit Conversions](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [() Operator](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eea3d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="eea3d-117">See Also</span></span>  
 [<span data-ttu-id="eea3d-118">TreeView コントロール</span><span class="sxs-lookup"><span data-stu-id="eea3d-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="eea3d-119">ListView コントロール</span><span class="sxs-lookup"><span data-stu-id="eea3d-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
