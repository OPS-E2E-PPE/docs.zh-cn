---
title: "程序集和全局程序集缓存 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2b98bd872bfdcbebb34fff3d878b92f39e27bbe0
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="assemblies-and-the-global-assembly-cache-c"></a><span data-ttu-id="bc35d-102">程序集和全局程序集缓存 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc35d-102">Assemblies and the Global Assembly Cache (C#)</span></span>
<span data-ttu-id="bc35d-103">程序集构成了 .NET 应用程序的部署、版本控制、重用、激活范围和安全权限的基本单元。</span><span class="sxs-lookup"><span data-stu-id="bc35d-103">Assemblies form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions for a .NET-based application.</span></span> <span data-ttu-id="bc35d-104">作为 .NET Framework 的构建基块，程序集采用可执行文件 (.exe) 或动态链接库文件 (.dll) 的形式。</span><span class="sxs-lookup"><span data-stu-id="bc35d-104">Assemblies take the form of an executable (.exe) file or dynamic link library (.dll) file, and are the building blocks of the .NET Framework.</span></span> <span data-ttu-id="bc35d-105">它们向公共语言运行时提供了注意类型实现代码所需的信息。</span><span class="sxs-lookup"><span data-stu-id="bc35d-105">They provide the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="bc35d-106">可以将程序集视为一组构成功能逻辑单元并旨在配合使用的类型和资源。</span><span class="sxs-lookup"><span data-stu-id="bc35d-106">You can think of an assembly as a collection of types and resources that form a logical unit of functionality and are built to work together.</span></span>  
  
 <span data-ttu-id="bc35d-107">程序集可以包含一个或多个模块。</span><span class="sxs-lookup"><span data-stu-id="bc35d-107">Assemblies can contain one or more modules.</span></span> <span data-ttu-id="bc35d-108">例如，可以将大型项目规划为，由多个开发者单独开发各个模块，最后将所有这些模块整合成一个程序集。</span><span class="sxs-lookup"><span data-stu-id="bc35d-108">For example, larger projects may be planned in such a way that several individual developers work on separate modules, all coming together to create a single assembly.</span></span> <span data-ttu-id="bc35d-109">有关模块的详细信息，请参阅主题[如何：生成多文件程序集](https://msdn.microsoft.com/library/226t7yxe)。</span><span class="sxs-lookup"><span data-stu-id="bc35d-109">For more information about modules, see the topic [How to: Build a Multifile Assembly](https://msdn.microsoft.com/library/226t7yxe).</span></span>  
  
 <span data-ttu-id="bc35d-110">程序集具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="bc35d-110">Assemblies have the following properties:</span></span>  
  
-   <span data-ttu-id="bc35d-111">程序集以 .exe 或 .dll 文件的形式实现。</span><span class="sxs-lookup"><span data-stu-id="bc35d-111">Assemblies are implemented as .exe or .dll files.</span></span>  
  
-   <span data-ttu-id="bc35d-112">可以将程序集放入全局程序集缓存，以便在应用程序之间共用程序集。</span><span class="sxs-lookup"><span data-stu-id="bc35d-112">You can share an assembly between applications by putting it in the global assembly cache.</span></span> <span data-ttu-id="bc35d-113">必须先为程序集命名强名称，然后才能将其添加到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="bc35d-113">Assemblies must be strong-named before they can be included in the global assembly cache.</span></span> <span data-ttu-id="bc35d-114">有关详细信息，请参阅[具有强名称的程序集](https://msdn.microsoft.com/library/wd40t7ad)。</span><span class="sxs-lookup"><span data-stu-id="bc35d-114">For more information, see [Strong-Named Assemblies](https://msdn.microsoft.com/library/wd40t7ad).</span></span>  
  
-   <span data-ttu-id="bc35d-115">只有在需要使用时才会将程序集加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="bc35d-115">Assemblies are only loaded into memory if they are required.</span></span> <span data-ttu-id="bc35d-116">如果不使用，就不会加载程序集。</span><span class="sxs-lookup"><span data-stu-id="bc35d-116">If they are not used, they are not loaded.</span></span> <span data-ttu-id="bc35d-117">也就是说，使用程序集，可以在大型项目中高效管理资源。</span><span class="sxs-lookup"><span data-stu-id="bc35d-117">This means that assemblies can be an efficient way to manage resources in larger projects.</span></span>  
  
-   <span data-ttu-id="bc35d-118">可以使用反射，以编程方式获取程序集的相关信息。</span><span class="sxs-lookup"><span data-stu-id="bc35d-118">You can programmatically obtain information about an assembly by using reflection.</span></span> <span data-ttu-id="bc35d-119">有关详细信息，请参阅[反射 (C#)](../../../../csharp/programming-guide/concepts/reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="bc35d-119">For more information, see [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md).</span></span>  
  
-   <span data-ttu-id="bc35d-120">如果想加载一个程序集以仅对其进行检查，请使用如 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 之类的方法。</span><span class="sxs-lookup"><span data-stu-id="bc35d-120">If you want to load an assembly only to inspect it, use a method such as <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.</span></span>  
  
## <a name="assembly-manifest"></a><span data-ttu-id="bc35d-121">程序集清单</span><span class="sxs-lookup"><span data-stu-id="bc35d-121">Assembly Manifest</span></span>  
 <span data-ttu-id="bc35d-122">每个程序集中都有*程序集清单*。</span><span class="sxs-lookup"><span data-stu-id="bc35d-122">Within every assembly is an *assembly manifest*.</span></span> <span data-ttu-id="bc35d-123">与目录类似，程序集清单包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="bc35d-123">Similar to a table of contents, the assembly manifest contains the following:</span></span>  
  
-   <span data-ttu-id="bc35d-124">程序集的标识（名称和版本）。</span><span class="sxs-lookup"><span data-stu-id="bc35d-124">The assembly's identity (its name and version).</span></span>  
  
-   <span data-ttu-id="bc35d-125">文件表，描述构成程序集的其他所有文件（例如，.exe 或 .dll 文件依赖的其他任何程序集、位图或自述文件）。</span><span class="sxs-lookup"><span data-stu-id="bc35d-125">A file table describing all the other files that make up the assembly, for example, any other assemblies you created that your .exe or .dll file relies on, or even bitmap or Readme files.</span></span>  
  
-   <span data-ttu-id="bc35d-126">*程序集引用列表*，列出了应用程序需要的可能由其他人创建的所有外部依赖项（.dll 或其他文件）。</span><span class="sxs-lookup"><span data-stu-id="bc35d-126">An *assembly reference list*, which is a list of all external dependencies—.dlls or other files your application needs that may have been created by someone else.</span></span> <span data-ttu-id="bc35d-127">程序集既可以引用全局对象，也可以引用私有对象。</span><span class="sxs-lookup"><span data-stu-id="bc35d-127">Assembly references contain references to both global and private objects.</span></span> <span data-ttu-id="bc35d-128">全局对象驻留在全局程序集缓存中，此区域对其他应用程序也可用。</span><span class="sxs-lookup"><span data-stu-id="bc35d-128">Global objects reside in the global assembly cache, an area available to other applications.</span></span> <span data-ttu-id="bc35d-129">私有对象必须位于级别不高于应用程序安装目录的目录中。</span><span class="sxs-lookup"><span data-stu-id="bc35d-129">Private objects must be in a directory at either the same level as or below the directory in which your application is installed.</span></span>  
  
 <span data-ttu-id="bc35d-130">由于程序集包含内容、版本控制和依赖项的相关信息，因此使用 C# 创建的应用程序不依赖 Windows 注册表值也能正常运行。</span><span class="sxs-lookup"><span data-stu-id="bc35d-130">Because assemblies contain information about content, versioning, and dependencies, the applications you create with C# do not rely on Windows registry values to function properly.</span></span> <span data-ttu-id="bc35d-131">程序集减少了 .dll 冲突，让应用程序变得更可靠、更易于部署。</span><span class="sxs-lookup"><span data-stu-id="bc35d-131">Assemblies reduce .dll conflicts and make your applications more reliable and easier to deploy.</span></span> <span data-ttu-id="bc35d-132">在许多情况下，只需将 .NET 应用程序的文件复制到目标计算机，即可进行安装。</span><span class="sxs-lookup"><span data-stu-id="bc35d-132">In many cases, you can install a .NET-based application simply by copying its files to the target computer.</span></span>  
  
 <span data-ttu-id="bc35d-133">有关详细信息，请参阅[程序集清单](https://msdn.microsoft.com/library/1w45z383)。</span><span class="sxs-lookup"><span data-stu-id="bc35d-133">For more information see [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="adding-a-reference-to-an-assembly"></a><span data-ttu-id="bc35d-134">添加对程序集的引用</span><span class="sxs-lookup"><span data-stu-id="bc35d-134">Adding a Reference to an Assembly</span></span>  
 <span data-ttu-id="bc35d-135">必须添加对程序集的引用，才能使用程序集。</span><span class="sxs-lookup"><span data-stu-id="bc35d-135">To use an assembly, you must add a reference to it.</span></span> <span data-ttu-id="bc35d-136">接下来，使用 [using 指令](../../../../csharp/language-reference/keywords/using-directive.md)选择要使用的项的命名空间。</span><span class="sxs-lookup"><span data-stu-id="bc35d-136">Next, you use the [using directive](../../../../csharp/language-reference/keywords/using-directive.md) to choose the namespace of the items you want to use.</span></span> <span data-ttu-id="bc35d-137">引用并导入程序集后，所有可访问的类、属性、方法和命名空间的其他成员都可供应用程序使用，就像其代码属于源文件一样。</span><span class="sxs-lookup"><span data-stu-id="bc35d-137">Once an assembly is referenced and imported, all the accessible classes, properties, methods, and other members of its namespaces are available to your application as if their code were part of your source file.</span></span>  
  
 <span data-ttu-id="bc35d-138">在 C# 中，还可以在单个应用程序中使用同一程序集的两个版本。</span><span class="sxs-lookup"><span data-stu-id="bc35d-138">In C#, you can also use two versions of the same assembly in a single application.</span></span> <span data-ttu-id="bc35d-139">有关详细信息，请参阅[外部别名](../../../../csharp/language-reference/keywords/extern-alias.md)。</span><span class="sxs-lookup"><span data-stu-id="bc35d-139">For more information, see [extern alias](../../../../csharp/language-reference/keywords/extern-alias.md).</span></span>  
  
## <a name="creating-an-assembly"></a><span data-ttu-id="bc35d-140">创建程序集</span><span class="sxs-lookup"><span data-stu-id="bc35d-140">Creating an Assembly</span></span>  
 <span data-ttu-id="bc35d-141">通过单击“生成”菜单上的“生成”或使用命令行编译器从命令行生成应用程序，从而编译应用程序。</span><span class="sxs-lookup"><span data-stu-id="bc35d-141">Compile your application by clicking **Build** on the **Build** menu or by building it from the command line using the command-line compiler.</span></span> <span data-ttu-id="bc35d-142">若要深入了解如何从命令行生成程序集，请参阅[使用 csc.exe 实现命令行生成](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="bc35d-142">For details about building assemblies from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc35d-143">若要在 Visual Studio 中生成程序集，请选择“生成”菜单上的“生成”。</span><span class="sxs-lookup"><span data-stu-id="bc35d-143">To build an assembly in Visual Studio, on the **Build** menu choose **Build**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc35d-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc35d-144">See Also</span></span>  
 <span data-ttu-id="bc35d-145">[C# 编程指南](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bc35d-145">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="bc35d-146">[公共语言运行时中的程序集](https://msdn.microsoft.com/library/k3677y81) </span><span class="sxs-lookup"><span data-stu-id="bc35d-146">[Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) </span></span>  
 <span data-ttu-id="bc35d-147">[友元程序集 (C#)](friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="bc35d-147">[Friend Assemblies (C#)](friend-assemblies.md) </span></span>  
 <span data-ttu-id="bc35d-148">[如何：与其他应用程序共享程序集 (C#)](how-to-share-an-assembly-with-other-applications.md) </span><span class="sxs-lookup"><span data-stu-id="bc35d-148">[How to: Share an Assembly with Other Applications (C#)](how-to-share-an-assembly-with-other-applications.md) </span></span>  
 <span data-ttu-id="bc35d-149">[如何：加载和卸载程序集 (C#)](how-to-load-and-unload-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="bc35d-149">[How to: Load and Unload Assemblies (C#)](how-to-load-and-unload-assemblies.md) </span></span>  
 <span data-ttu-id="bc35d-150">[如何：确定文件是否为程序集 (C#)](how-to-determine-if-a-file-is-an-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="bc35d-150">[How to: Determine If a File Is an Assembly (C#)](how-to-determine-if-a-file-is-an-assembly.md) </span></span>  
 <span data-ttu-id="bc35d-151">[如何：使用命令行创建和使用程序集 (C#)](how-to-create-and-use-assemblies-using-the-command-line.md) </span><span class="sxs-lookup"><span data-stu-id="bc35d-151">[How to: Create and Use Assemblies Using the Command Line (C#)](how-to-create-and-use-assemblies-using-the-command-line.md) </span></span>  
 <span data-ttu-id="bc35d-152">[演练：在 Visual Studio 中嵌入托管程序集中的类型 (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="bc35d-152">[Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)](walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) </span></span>  
 [<span data-ttu-id="bc35d-153">演练：在 Visual Studio 中嵌入 Microsoft Office 程序集中的类型信息 (C#)</span><span class="sxs-lookup"><span data-stu-id="bc35d-153">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>](walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
