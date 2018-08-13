[source](https://dev.to/aershov24/11-painful-git-interview-questions-you-will-cry-on-1n2g)

## 11 câu hỏi phỏng vấn về Git khiến bạn phải khóc thét

Theo khảo sát phát triển Stack Overflow mới nhất, hơn 70% các nhà phát triển sử dụng Git, biến nó trở thành VCS được sử dụng nhiều nhất trên thế giới. Git thường được sử dụng cho cả phát triển phần mềm thương mại và nguồn mở, với những lợi ích đáng kể cho các cá nhân, nhóm và doanh nghiệp.

### Q1: Git fork là gì? sự khác biệt giữa fork, branch và clone?

* Một fork là một remote, một bản sao chép của repository trên phía server, nhưng nó lại khác với bản gốc. Một fork không thực sự được coi là khái niệm của git, nó giống như là một ý tưởng về chính trị/xã hội hơn.
* Một clone thì không phải là một fork, một clone là bản sao chép của một remote repository nào đó. Khi bạn clone, thực ra bạn chỉ sao chép mã nguồn của repository đó, bao gồm tất cả lịch sử và các nhánh.
* A branch is a mechanism to handle the changes within a single repository in order to eventually merge them with the rest of code. A branch is something that is within a repository. Conceptually, it represents a thread of development.
* Một nhánh là một cơ chế để xử lý các thay đổi trong một repository duy nhất để cuối cùng merge chúng với phần còn lại của code. Branch là cái gì đó nằm trong một repository. Về mặt khái niệm, nó đại diện cho một luồng phát triển.

### Q2: Điểm khác biệt giữa một "pull request" và một "branch"?

* Branch chỉ là một phiên bản riêng biệt của code.

* Một pull request là khi có ai đó lấy một repository, tạo ra nhánh của riêng họ, thực hiện một vài thay đổi, và cố gắng merge các nhánh trong đó (đưa những thay đổi của họ vào code trên repository của người khác)

### Q3: Sự khác biệt giữa "git pull" và "git fetch" là gì?

Nói một cách đơn giản, git pull thực hiện một git fetch và theo sau đó là một git merge.

* Khi bạn sử dụng pull, Git sẽ cố gắng tự động thực hiện công việc cho bạn. Đó là trường hợp khá nhạy cảm, vì vậy Git sẽ hợp nhất bất kỳ pull commit vào nhánh bạn đang làm việc. Pull tự động kết hợp các commit mà không cho bạn xem lại chúng trước. Nếu bạn không quản lý chặt chẽ các branch của mình, bạn có thể thường xuyên gặp phải các xung đột.

* When you fetch, Git gathers any commits from the target branch that do not exist in your current branch and stores them in your local repository. However, it does not merge them with your current branch. This is particularly useful if you need to keep your repository up to date, but are working on something that might break if you update your files. To integrate the commits into your master branch, you use merge.

*Khi bạn fetch, Git thu thập bất kỳ commit nào từ nhánh đích mà không tồn tại trong nhánh hiện tại của bạn và lưu trữ chúng trong local repository của bạn. Tuy nhiên, nó không merge chúng với branch hiện tại của bạn. Điều này đặc biệt hữu ích nếu bạn cần cập nhật repository của bạn, nhưng khi đang làm việc trên thứ gì đó, nó có thể bị lỗi nếu bạn cập nhật các file của mình. Để tích hợp các commit vào nhánh chính của bạn, bạn sử dụng merge.

### Q4: Làm thế nào để quay lại commit trước đó trong git?


Giả sử bạn có sơ đồ này, trong đó C là HEAD của bạn và (F) là trạng thái tệp của bạn.

```
   (F)
A-B-C
    ↑
  master
```

* Để quay lại các thay đổi trong commit:

```
git reset --hard HEAD~1
```

Bây giờ B là con trỏ HEAD. Vì bạn sử dụng --hard, các file của bạn đã bị reset về trạng thái của commit B.

* Để quay lại commit nhưng vẫn giữ lại các thay đổi của bạn:

```
git reset HEAD~1
```

Bây giờ chúng tôi yêu cầu Git di chuyển con trỏ HEAD trở lại một cam kết (B) và để lại các tập tin như họ đang có và trạng thái git cho thấy những thay đổi bạn đã kiểm tra vào C.

* Để quay lại một commit của bạn nhưng bỏ lại các file và các index của bạn: 

```
git reset --soft HEAD~1
```

### Q5: "git cherry-pick" là gì?

The command git cherry-pick is typically used to  particular commits from one branch within a repository onto a different branch. A common use is to forward- or back-port commits from a maintenance branch to a development branch.
Lệnh git cherry-pick thường được sử dụng để đưa vào các commit cụ thể từ một nhánh trong một repository trên một branch khác. Việc sử dụng phổ biến là chuyển tiếp hoặc vá lại các commit từ maintenance branch bảo trì đến development branch.

Điều này ngược lại với các cách khác như merge và rebase mà thường áp dụng nhiều commit vào một nhánh khác.
Chú ý:

```
git cherry-pick <commit-hash>
```

### Q6: Giải thích những ưu điểm của Forking Workflow

Một Forking Workflow cơ bản khác với workflow phổ biến khác của Git. Thay vì sử dụng một repository phía server duy nhất để hoạt động như là cơ sở dữ liệu "trung tâm", nó cung cấp cho mỗi nhà phát triển repository phía server của riêng họ. Forking Workflow thường được thấy nhất trong các dự án nguồn mở công khai.

Ưu điểm chính của Forking Workflow là các đóng góp có thể được tích hợp mà không cần mọi người đẩy vào một repository trung tâm duy nhất nên sẽ tạo ra một lịch sử sạch sẽ cho dự án. Các nhà phát triển push lên repository phía server của riêng họ và chỉ người duy trì dự án mới có thể push lên repository chính thức.

Khi các nhà phát triển sẵn sàng xuất bản một local commit, họ push commit vào public repository của riêng họ — không phải là repository chính thức. Sau đó, họ gửi pull request với repository chính, cho phép người duy trì dự án biết rằng bản cập nhật đã sẵn sàng để được tích hợp.

### Q7: Cho tôi biết sự khác biệt giữa HEAD, working tree và index, trong Git?

* Một cây công việc/ thư mục công việc/ phân vùng làm việc là một dạy cây thư mục của các file(nguồn) mà bạn có thể nhìn thấy và chỉnh sửa.
* Vùng index/staging là một tệp nhị phân lớn, duy nhất trong /.git/index, liệt kê tất cả các file trong branch hiện tại, các đoạn sha1 checksums, mã thời gian và tên file - nó không phải là một thư mục khác có bản sao các file trong đó.
* HEAD là tham chiếu đến lần commit cuối cùng trong branch hiện đã được kiểm tra.

### Q8: Bạn có thể giải thích về Gitflow Worrkflow được không?

Gitflow workflow employs two parallel long-running branches to record the history of the project, master and develop:
 Gitflow workflow sử dụng hai nhánh chạy song song để ghi lại lịch sử của dự án, là master và develop:
* Master - luôn sẵn sàng để được phát hành trên LIVE, với mọi thứ đã được kiểm tra và phê duyệt đầy đủ (production ready).

  * Hotfix - Các nhánh bảo trì hoặc “hotfix” được sử dụng để nhanh chóng vá các bản phát hành sản phẩm. Các nhánh Hotfix rất giống các nhánh release và các nhánh tính năng trừ khi chúng dựa trên master thay vì develop.

* Develop - là nhánh mà tất cả các nhánh tính năng được merge vào và nơi tất cả các kiểm nghiệm được thực hiện. Chỉ khi mọi thứ được kiểm tra kỹ lưỡng và sửa chữa thì nó có thể được merge vào nhánh master.

  * Feature - Mỗi tính năng mới phải nằm trong branch riêng của nó, có thể được push tới nhánh develop như một nhánh cha của chúng.

![](https://res.cloudinary.com/practicaldev/image/fetch/s--pLQxGakq--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%2520%282%29.svg%3FcdnVersion%3Dji)

### Q9: When should I use "git stash"?
### Q9: Khi nào thì ta nên sử dụng "git stash"?

The `git stash` command takes your uncommitted changes (both staged and unstaged), saves them away for later use, and then reverts them from your working copy.
Lệnh `git stash` lấy các thay đổi chưa được commit của bạn (trong cả staged và unstaged), lưu chúng lại để sau này sử dụng, sau đó revert chúng tại phiên bản working của bạn.
Xem qua:

```
$ git status
On branch master
Changes to be committed:
new file: style.css
Changes not staged for commit:
modified: index.html
$ git stash
Saved working directory and index state WIP on master: 5002d47 our new homepage
HEAD is now at 5002d47 our new homepage
$ git status
On branch master
nothing to commit, working tree clean
```

Chúng ta có thể sử dụng stash khi chúng ta phát hiện ra rằng chúng ta quên gì đó trong commit cuối và bắt đầu làm việc trên cái tiếp theo tại cùng 1 nhánh đó:

```
# Assume the latest commit was already done
# start working on the next patch, and discovered I was missing something

# stash away the current mess I made
$ git stash save

# some changes in the working dir

# and now add them to the last commit:
$ git add -u
$ git commit --ammend

# back to work!
$ git stash pop
```

### Q10: Làm sao để xoá một file từ git mà không xoá file đó trên hệ thống file của bạn?

If you are not careful during a git add, you may end up adding files that you didn’t want to commit. However, git rm will remove it from both your staging area (index), as well as your file system (working tree), which may not be what you want.
Nếu bạn không cẩn thận trong khi thêm git, bạn có thể sẽ thêm các tệp mà bạn không muốn commit. Tuy nhiên, `git rm` sẽ xóa nó khỏi cả phân vùng stage (index) của bạn, cũng như hệ thống file của bạn (working tree), có thể không phải là thứ bạn muốn.

thay vào đó hãy sử dụng ``git reset``:

```
git reset filename          # or
echo filename >> .gitingore # add it to .gitignore to avoid re-adding it
```

điều này có nghĩa là `git reset <paths>` ngược lại với `git add <paths>`.

### Q11: Khi nào bạn sử dụng "git rebase" thay cho "git merge"?

Cả hai lệnh này được thiết kế để tích hợp các thay đổi từ một branch này sang một branch khác - chúng chỉ thực hiện theo những cách khác nhau thôi.

xem lại trước khi merge/rebase:

```
A <- B <- C    [master]
^
 \
  D <- E       [branch]
```

sau khi  `git merge master`:

```
A <- B <- C
^         ^
 \         \
  D <- E <- F
```

sau khi  `git rebase master`:

```
A <- B <- C <- D <- E
```

Với rebase bạn hiểu là sử dụng một branch khác như một phần base mới cho công việc của bạn.


##### Sử dụng khi nào:

1. Nếu bạn không chắc chắn về nó, hãy sử dụng merge.
2. lựa chọn rebase hoặc merge dựa trên những gì bạn muốn history của bạn trông như thế nào.

##### Một số yếu tố khác cần xem xét:

1. Branch của bạn có đang nhận được các thay đổi từ việc chia sẻ với các nhà phát triển khác bên ngoài nhóm của bạn (ví dụ: nguồn mở, công khai) không? Nếu vậy, đừng rebase. Rebase phá hủy các branch và các developer đó sẽ có các repository bị hỏng hoặc không nhất quán trừ khi họ sử dụng lệnh git pull --rebase.
2. Đội ngũ phát triển của bạn có kỹ năng như thế nào? Rebase là một hoạt động mang tính phá huỷ. Điều đó có nghĩa là, nếu bạn không áp dụng nó một cách chính xác, bạn có thể mất các commit và / hoặc phá vỡ sự thống nhất của repository của developer khác.
3.Branch có thông tin hữu ích không? Một số nhóm sử dụng mô hình branch-per-feauture, trong đó mỗi branch đại diện cho một tính năng cụ thể (hoặc bugfix, hoặc tính năng phụ, vv) Trong mô hình này branch giúp xác định tập hợp các commit có liên quan. Trong trường hợp mô hình branch-per-feature, chính branch đó không truyền tải bất kỳ thông tin bổ sung nào (commit đã có tác giả). Sẽ không gây hại gì khi rebasing.
4. Bạn có muốn revert lại các merge vì bất kỳ lý do nào không? revert (như là undoing) một rebase rất khó khăn và / hoặc không thể (nếu rebase có xung đột) so với revert một merge. Nếu bạn muốn có cơ hội để có thể revert, hãy sử dụng merge.
