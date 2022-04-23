---
title: Thêm CMS vào trang web tĩnh của bạn với Netlify CMS
date: April 22, 2022 12:35 AM
---
<!--StartFragment-->

Trong gần bảy năm, tôi là người triển khai và đóng góp CMS, chủ yếu là với Drupal, nhưng đôi khi với Joomla! và WordPress. Sau đó, khoảng 3 năm trước, tôi gặp Jekyll và tôi đã có một tiết lộ, một hệ thống cho phép tôi quản lý và hiển thị nội dung, nhưng theo cách phù hợp với tôi với tư cách là một nhà văn, sử dụng các định dạng đánh dấu như markdown, reStructuredText và Asciidoc. Mặc dù cách tiếp cận kiểm soát phiên bản và văn bản thuần túy là tuyệt vời đối với một số người và mặc dù đã có những nỗ lực tốt nhất từ ​​các nhà cung cấp như GitHub và GitLab, nhưng nó vẫn không thể tiếp cận được với những người kém kỹ thuật. Nhiều dự án đã cố gắng thu hẹp khoảng cách này và hợp nhất những gì tốt nhất của hai thế giới, từ các nhà cung cấp SaaS thương mại như [Contentful](https://www.contentful.com/) , [Prismic](https://prismic.io/) hoặc [CloudCannon](https://cloudcannon.com/) đến các tùy chọn nguồn mở như[Buồng lái](https://getcockpit.com/) và [getmesh](https://getmesh.io/) .

Chỉ hơn một năm trước, [Netlify](https://www.netlify.com/) , công ty lưu trữ tuyệt vời cho các trang web tĩnh đã công bố ' [Netlify CMS](https://www.netlifycms.org/docs/) ' và nó có vẻ đầy hứa hẹn, bổ sung giao diện giống CMS vào quy trình làm việc git. Tôi đã thực hiện một số điều tra ban đầu, nhưng bây giờ cuối cùng đã có thời gian để đi sâu vào cách thiết lập và sử dụng nó.

Tôi sẽ sử dụng Netlify CMS (NC) với Jekyll, nhưng bạn có thể tìm thấy hướng dẫn về cách thêm nó vào [các trang tĩnh hiện có khác](https://www.netlifycms.org/docs/add-to-your-site) hoặc [bắt đầu lại từ đầu với một trang mới](https://www.netlifycms.org/docs/start-with-a-template/) .

## Thêm Netlify CMS vào Jekyll

Tạo một thư mục *quản trị* với một *tệp index.html* và một tệp *config.yml* ; những thứ này đóng vai trò là cổng vào giao diện quản trị của bạn và các cài đặt đằng sau nó, tương ứng.

Bên trong *index.html* , thêm khung HTML, JavaScript và CSS cần thiết để tạo giao diện quản trị, để xây dựng thương hiệu tùy chỉnh đầy đủ, bạn cũng có thể thêm liên kết vào trang định kiểu của mình, nhưng vì đây là 'phụ trợ' quản trị viên, bạn có thể không cần chúng.

```

```

Đương nhiên, tệp cấu hình khác nhau tùy theo trường hợp sử dụng của bạn, nhưng tôi sẽ chỉ cho bạn những gì tôi sử dụng cho trang web ' [Gregarious Mammal](https://www.gregariousmammal.com/) ' của mình và bạn có thể ngoại suy từ đó.

Đầu tiên, xác định loại phụ trợ và nếu người dùng cần xác thực để truy cập nó, bạn có thể sử dụng người dùng được xác định trong Netlify hoặc trong GitHub (những người có quyền truy cập đẩy). Tôi muốn cho phép người dùng thay đổi nội dung bên ngoài Netlify, vì vậy hãy sử dụng phương pháp GitHub:

```

```

Để xác định người dùng nào có thể truy cập phần phụ trợ quản trị và chỉnh sửa nội dung, tôi khuyên bạn nên đọc [các bước của Netlify](https://www.netlifycms.org/docs/add-to-your-site/#authentication) . Bạn có thể xác thực bằng [nhiều phương pháp khác nhau](https://www.netlifycms.org/docs/authentication-backends) hoặc xử lý quy trình thông qua dịch vụ nhận dạng của Netlify mà bạn có thể đã thiết lập (tôi thì có).

Nếu bạn thêm cài đặt bên dưới, thì các bài đăng sẽ trải qua một quy trình công việc trong đó người dùng cụ thể có thể xem xét và chỉnh sửa các bài đăng được giữ trong các yêu cầu kéo cho đến khi bạn xuất bản chúng. Nếu không, NC cam kết các bài đăng đến nhánh được xác định ở trên.

```

```

![Thêm CMS vào trang web tĩnh của bạn với Netlify CMS](https://cdn.helpex.vn/upload/2018/01/03/05-00-00-000-cc7a0e5c-9cff-4b3a-aab4-06073ea38699.jpg)

Trang web sử dụng rất nhiều hình ảnh và tôi muốn mọi người thêm một hình ảnh vào mỗi bài đăng, vì vậy bạn cần xác định nơi lưu trữ chúng, thêm `media_folder`thông số đó bằng tham số và cũng có `public_folder`thể đặt nơi phân phát hình ảnh:

```

```

Tôi đã tìm thấy một số vấn đề với hình ảnh mà tôi đã lưu trữ trong các thư mục con, [có một vấn đề khi](https://github.com/netlify/netlify-cms/issues/513) thảo luận về các thư mục con, nhưng tôi không chắc liệu nó có liên quan hay không.

![Thêm CMS vào trang web tĩnh của bạn với Netlify CMS](https://cdn.helpex.vn/upload/2018/01/03/05-00-00-000-58bf92e1-a90f-43a6-b9fa-174d5be9850d.jpg)

Bây giờ đến phần phức tạp nhất. Trang web của tôi có rất nhiều 'loại nội dung' khác nhau để đại diện cho các mục nội dung khác nhau, đôi khi sử dụng bộ sưu tập và đôi khi sử dụng các trường khác nhau ở những nơi khác nhau. Phần này sẽ là phần cấu hình của bạn và bao gồm một loạt các phần YAML đại diện cho nội dung của bạn. Cấu trúc chung là:

```

```

Bạn có thể sử dụng một trong khoảng [12 widget mặc định](https://www.netlifycms.org/docs/widgets/) và không quá khó để [tạo ](https://www.netlifycms.org/docs/custom-widgets/)[widget ](https://www.netlifycms.org/docs/widgets/)[của riêng](https://www.netlifycms.org/docs/custom-widgets/) bạn nếu bạn biết React. Theo mặc định, các trường được đặt là `required`, vì vậy hãy thêm `required: false`nếu chúng không có trong mô hình nội dung của bạn, tức là:

```

```

Trang web của tôi có rất nhiều nội dung và tôi không thể tải Netlify CMS để tải tất cả - đây có thể là giới hạn với các lệnh gọi JavaScript hoặc API GitHub. Có thể có một cách để khắc phục điều này, nhưng vì nhiều bài đăng là tệp gốc được tạo tự động cho nội dung tổng hợp, tôi không cần phải chỉnh sửa chúng. Netlify CMS cung cấp một cách để lọc chúng bằng cách sử dụng thuộc `filter`tính trên một giá trị trường.

```

```

Tôi muốn lọc theo ngày để tải các bài đăng gần đây nhất, nhưng điều đó không thể thực hiện được, vì vậy tôi đã cố gắng lọc các bài đăng không có `publication_url`nhưng không có nhiều may mắn để bộ lọc hoạt động, số dặm của bạn có thể thay đổi. Cũng có những giới hạn về số lượng bạn có thể lấy từ API GitHub, vì vậy tôi có thể cần tổ chức lại nội dung của mình thành nhiều bộ sưu tập hoặc thư mục con hơn.

Bạn có thể xem các loại nội dung hoàn chỉnh cho trang web của tôi tại [đây](https://github.com/GregariousMammal/Main-Site/blob/master/admin/config.yml) .

## Sử dụng Netlify CMS

Kích hoạt trình tạo trang web tĩnh của bạn như bình thường và truy cập *_admin* . Bạn sẽ thấy các phần cho từng loại nội dung mà bạn đã xác định, cùng với một phần cho phương tiện và quy trình làm việc (nếu được bật).

![Thêm CMS vào trang web tĩnh của bạn với Netlify CMS](https://cdn.helpex.vn/upload/2018/01/03/05-00-00-000-e9eec7c9-321c-41ed-b3e0-7345ea20abc2.jpg)

Giao diện có các tùy chọn bộ lọc và sắp xếp hạn chế, nhưng có một hộp tìm kiếm. Bạn sử dụng các nút *thêm* để tạo nội dung với GUI tiện dụng và xem trước nó. Khi bạn nhấp vào *lưu* , các bài đăng được giữ trong một yêu cầu kéo cho đến khi bạn xuất bản chúng khi chúng được hợp nhất vào trang chính. [Có một bản tóm tắt ở đây](https://www.netlifycms.org/docs/configuration-options#publish-mode) về hành động GUI dẫn đến hành động git nào.

![Thêm CMS vào trang web tĩnh của bạn với Netlify CMS](https://cdn.helpex.vn/upload/2018/01/03/05-00-00-000-b2195056-5c2c-472c-b4aa-0dd926dca4c8.jpg)

![Thêm CMS vào trang web tĩnh của bạn với Netlify CMS](https://cdn.helpex.vn/upload/2018/01/03/05-00-00-000-2da9b426-c62d-4e5a-815c-11eefd145736.jpg)

## SSCMS (CMS trang web tĩnh!)

Theo tôi, cho đến nay, Netlify đã nỗ lực hết sức để tạo ra giao diện người dùng giống CMS cho các trang web tĩnh phù hợp với quy trình làm việc của người dùng kỹ thuật và phi kỹ thuật. Đó là những ngày đầu với các lỗi và tính năng cần thiết, nhưng với sức mạnh của sản phẩm thương mại Netlify và ổ đĩa cộng đồng, tôi có rất nhiều hy vọng cho sự phát triển của nó.

* [cms](https://helpex.vn/it-code/bai-viet-chu-de/cms)
* [content-management-system](https://helpex.vn/it-code/bai-viet-chu-de/content-management-system)
* [static site generator](https://helpex.vn/it-code/bai-viet-chu-de/static-site-generator)
* [git](https://helpex.vn/it-code/bai-viet-chu-de/git)
* [web dev](https://helpex.vn/it-code/bai-viet-chu-de/web-dev)

15 hữu ích0 bình luận14k xemchia sẻ

[ ](javascript:void(0) "Facebook Share")[ ](javascript:void(0) "Twitter Share")[](javascript:void(0) "E-Mail Share")

## CÓ THỂ BẠN QUAN TÂM

# [GitLab trên SSGs: Gặp gỡ tĩnh và động ở giữa](https://helpex.vn/article/gitlab-tren-ssgs-gap-go-tinh-va-dong-o-giua-60c99e6d3f07bf0a5af5b7e9)

![Hoàng Lam Bích](https://cdn.helpex.vn/upload/2017/10/11/55ee42f98b75f32e341507cb-075337946_50x50.jpg)

[Hoàng Lam Bích](https://helpex.vn/thanh-vien/55ee42f98b75f32e341507cb)·17:00 23/06/2016

2 ngày trước

Gần đây, đã có một số bài đăng thực sự xuất sắc trên [GitLab](https://about.gitlab.com/blog/) về sự [khác biệt giữa trang web tĩnh và trang web động](https://about.gitlab.com/2016/06/03/ssg-overview-gitlab-pages-part-1-dynamic-x-static/) , thông tin chi tiết [của trình tạo trang web tĩnh (SSG)](https://about.gitlab.com/2016/06/10/ssg-overview-gitlab-pages-part-2/) và [việc sử dụng Trang GitLab kết hợp với SSG](https://about.gitlab.com/2016/06/17/ssg-overview-gitlab-pages-part-3-examples-ci/) . Trong bài đăng này, tôi dự định tổng hợp loạt bài này, đưa ra một số thông tin chi tiết chính mà GitLab đã cung cấp.

Chúng ta hãy đi đến đó!

## Trang web tĩnh so với trang web động

Các trang web tĩnh hoạt động giống như tên cho thấy ... chúng không thay đổi. Chúng được ghi vào một tệp một lần và nội dung bên trong chúng được giữ nguyên trừ khi tệp được mở ra và sửa đổi trực tiếp.

Các trang web này được xây dựng từ một tập hợp các đánh dấu HTML, CSS và JavaScript. Chúng được lưu trữ dưới dạng các tệp đơn giản trên máy chủ và được máy khách từ xa truy cập thông qua trình duyệt web. Luồng có thể được mô tả như sau:

* Người dùng cho trình duyệt web biết họ muốn gì.
* Trình duyệt gửi một yêu cầu HTTP đến máy chủ web.
* Máy chủ hiểu yêu cầu đó và trả lại dữ liệu cho trình duyệt (và do đó, người dùng) bằng phản hồi HTTP.

![GitLab trên SSGs: Gặp gỡ tĩnh và động ở giữa](https://cdn.helpex.vn/upload/2016/06/23/05-00-00-000-7333e182-3fe6-46cd-9a11-031c6632e1e8.jpg)

##### *Hình ảnh từ bài đăng của GitLab: [SSGs Phần 1: Trang web tĩnh và trang web động](https://about.gitlab.com/2016/06/03/ssg-overview-gitlab-pages-part-1-dynamic-x-static/)*

\
Mặc dù cũng được xây dựng từ đánh dấu HTML, CSS và JavaScript, các trang web động hoạt động hơi khác một chút. Một lần nữa, giống như tên cho thấy, các trang web này có thể thay đổi tùy thuộc vào các nguồn bên ngoài mà chúng lấy dữ liệu từ đó. Các tệp của họ phức tạp hơn và cơ sở dữ liệu tham khảo để biết thông tin cụ thể. Nếu thông tin trong cơ sở dữ liệu bị thay đổi, thì thông tin tương ứng trên một trang động cũng thay đổi theo. Luồng có thể được mô tả như sau:

* Người dùng cho trình duyệt web biết họ muốn gì.
* Trình duyệt gửi một yêu cầu HTTP đến máy chủ web.
* Máy chủ không thể tự hiểu yêu cầu đó, nhưng được yêu cầu chuyển yêu cầu đến máy chủ ứng dụng.
* Máy chủ ứng dụng lấy thông tin được yêu cầu từ cơ sở dữ liệu, trả dữ liệu trở lại máy chủ web và cuối cùng trở lại trình duyệt (và do đó, người dùng) bằng phản hồi HTTP.

![GitLab trên SSGs: Gặp gỡ tĩnh và động ở giữa](https://cdn.helpex.vn/upload/2016/06/23/05-00-00-000-aad0bc7b-bbb1-4bd4-bbcb-32295f634764.jpg)

##### *Hình ảnh từ bài đăng của GitLab: [SSGs Phần 1: Trang web tĩnh và trang web động](https://about.gitlab.com/2016/06/03/ssg-overview-gitlab-pages-part-1-dynamic-x-static/)*



Một trong những phần yêu thích của tôi về phạm vi bảo hiểm của GitLab về các trang web tĩnh và động đã tiết lộ một chút về lịch sử của web. Họ đã liên kết với [trang web đầu tiên từng được tạo — ra](http://info.cern.ch/hypertext/WWW/TheProject.html) đời vào năm 1990, trang web tĩnh này không có nhiều hoạt động so với các trang web ngày nay. Và, cũng như đã lưu ý trong bài báo, ba năm sau, trang web động đầu tiên đã xuất hiện nhờ sự ra đời của  [Giao diện cổng chung](https://en.wikipedia.org/wiki/Common_Gateway_Interface) .

### Ưu và nhược điểm

Hãy thảo luận về những ưu điểm và nhược điểm khác nhau của từng loại trang web dưới đây ...

#### Trang web tĩnh

|                                                                                               |                                                                                                                   |
| --------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Ưu điểm**                                                                                   | **Nhược điểm**                                                                                                    |
| thời gian tải nhanh                                                                           |                                                                                                                   |
| an toàn hơn cho người dùng — không có thông tin nào được gửi từ máy khách, chỉ được truy xuất | ít tương tác hơn được phép vì thông tin không được gửi từ máy khách — chỉ các siêu liên kết mới có tính tương tác |
| đơn giản để phát triển (đối với các trang web nhỏ với thiết kế không phức tạp)                |                                                                                                                   |
|                                                                                               |                                                                                                                   |

#### Trang web động

|                                                             |                                                                                |
| ----------------------------------------------------------- | ------------------------------------------------------------------------------ |
| **Ưu điểm**                                                 | **Nhược điểm**                                                                 |
| Lỗi mã hóa ít xảy ra hơn vì giảm thiểu việc lặp lại mã hóa  |                                                                                |
| cho phép người dùng tương tác nhiều hơn với một trang web   | rủi ro hơn cho người dùng — dữ liệu thường được gửi từ người dùng đến máy chủ  |
|                                                             | yêu cầu nhiều mã hóa hơn ngay từ đầu                                           |
|                                                             |                                                                                |

Tóm lại, nếu bạn đang tìm cách tạo một trang web nhỏ, đơn giản, sử dụng một lần, không yêu cầu nhiều tương tác từ người dùng — chỉ đọc — thì một trang tĩnh có thể là đủ. Tuy nhiên, nếu bạn đang hy vọng tạo một trang web tương tác có khả năng cần thay đổi sau này, bạn rất có thể muốn có một trang web động.

Hoặc, nếu bạn muốn kết hợp cả hai, thì có thể trình tạo trang web tĩnh (SSG) là thứ bạn đang theo đuổi ...

## Trình tạo trang web tĩnh (SSG)

SSG là phần mềm được thiết kế để cho phép các nhà phát triển web có khả năng mã động trên nhiều trang web trong một lần thao tác nhanh trong khi xuất ra những thay đổi này để tạo ra các trang web tĩnh riêng lẻ.

Các trang web này cung cấp hầu hết các đặc quyền của các trang web động (khả năng viết mã nhanh và cung cấp *hầu hết* các trang web tương tác) trong khi tránh được nhiều sự cố khác nhau của chúng (nặng về hiệu suất, xử lý phía máy chủ và lưu trữ web đắt tiền).

Đó là sự kết hợp của các tính năng này cho phép các SSG hoạt động:

* **Engine / Platform -** được tạo thành từ ngôn ngữ lập trình mà engine được tạo ra; cho phép SSG có các đặc điểm khác nhau
* **Công cụ mẫu -** cho phép các chất lượng động như thay đổi sâu rộng trên nhiều trang web tĩnh
* **Đánh dấu -** một hệ thống để viết tài liệu và phân biệt mã với văn bản
* **Bộ tiền xử lý -** tăng tốc quá trình mã hóa
* **Thư mục -** cấu trúc tệp khác nhau cho các SSG khác nhau

Nếu bạn muốn có một cái nhìn tổng quan kỹ lưỡng hơn về những điều này, tôi khuyên bạn nên xem [ở đây](https://about.gitlab.com/2016/06/10/ssg-overview-gitlab-pages-part-2/#structure-of-ssgs) .

Mặc dù rõ ràng là SSG có rất nhiều ưu điểm, nhưng tôi vẫn chưa nói về nhược điểm của chúng ...

* Họ không cung cấp khả năng đăng ký người dùng hoặc cung cấp các tính năng quản trị viên.
* Họ không cung cấp khả năng gửi email bằng cách sử dụng hàm **mail ()**  .
* Họ không cho phép sử dụng bất kỳ ngôn ngữ hoặc tập lệnh phía máy chủ nào.   

May mắn thay, có những [giải pháp](https://about.gitlab.com/2016/06/10/ssg-overview-gitlab-pages-part-2/#overcoming-the-limitations) thay thế cho những điều này.

## SSG và Trang GitLab

Vậy, mối liên hệ giữa SSG và GitLab là gì?

![GitLab trên SSGs: Gặp gỡ tĩnh và động ở giữa](https://cdn.helpex.vn/upload/2016/06/23/05-00-00-000-37ea95d8-055b-43c7-9716-2d98c0858e08.jpg)

Với [GitLab Pages](https://pages.gitlab.io/) , bạn có thể lưu trữ và tạo miễn phí [bất kỳ SSG nào](https://www.staticgen.com/) trên mạng. Và, họ cung cấp cho bạn [rất nhiều ](https://about.gitlab.com/2016/04/07/gitlab-pages-setup/) [các  ](https://pages.gitlab.io/)[tài liệu](http://docs.gitlab.com/ee/pages/README.html)  trong trường hợp bạn gặp bất kỳ khó khăn trong quá trình này. Như GitLab tuyên bố, bạn có thể "sử dụng miền tùy chỉnh, chứng chỉ SSL / TLS, tạo bao nhiêu trang web tùy thích và triển khai trang web của bạn từ các kho lưu trữ riêng tư."

Bạn muốn xem một số ví dụ về SSG được lưu trữ trên GitLab? Kiểm tra bảng [tiện dụng](https://about.gitlab.com/2016/06/17/ssg-overview-gitlab-pages-part-3-examples-ci/#ssgs-examples) này  [về các trang SSG được xây dựng bằng Trang GitLab](https://about.gitlab.com/2016/06/17/ssg-overview-gitlab-pages-part-3-examples-ci/#ssgs-examples)  với mỗi mục nhập được sắp xếp theo môi trường mà nó được tạo.

## Kết thúc

Việc GitLab lưu trữ miễn phí các SSG với GitLab Pages khiến tôi cảm thấy không quá ... mặc dù điều đó khá tuyệt. Thay vào đó, tôi rất hài lòng với cách họ mở lòng với cộng đồng của mình trong [loạt bài này](https://about.gitlab.com/2016/06/03/ssg-overview-gitlab-pages-part-1-dynamic-x-static/) .

Tôi thực sự thích quy trình tổng thể ở đây — kể về lịch sử đằng sau các trang web tĩnh và động (và Web nói chung), tìm hiểu các khái niệm cơ bản về SSG và quay trở lại cách tất cả điều này liên quan đến GitLab. Tôi phải ghi nhận công lao của [Marcia Ramos](https://twitter.com/virtuacreative)  vì đã viết một bộ truyện hay (hoàn toàn thú vị) như vậy.

Ngoài ra, tôi đặc biệt vui mừng khi đọc nhận xét này từ một nhân viên GitLab cho một độc giả cảm thấy bộ truyện quá sơ đẳng ...

![GitLab trên SSGs: Gặp gỡ tĩnh và động ở giữa](https://cdn.helpex.vn/upload/2016/06/23/05-00-00-000-266b33a8-fe88-4600-b117-c7ef95ce811d.jpg)

Tôi thực sự thích tình cảm này vì điều này cho thấy môi trường hòa nhập mà GitLab đang cố gắng thúc đẩy — một môi trường mà chúng tôi cũng cố gắng thúc đẩy ở đây tại DZone. Mặc dù họ rõ ràng là hướng đến các nhà phát triển, GitLab cũng mở cửa cho những người mới bắt đầu hoặc thậm chí những người nằm ngoài phạm vi điển hình của các nhà phát triển và lập trình viên. Và, tôi nghĩ rằng đây luôn là cách tiếp cận tốt nhất. Rốt cuộc, mọi người phải bắt đầu từ đâu đó.  

Hãy theo [dõi blog GitLab](https://about.gitlab.com/blog/)  để biết thêm những bài viết tuyệt vời như thế này! Và, hãy cân nhắc việc sử dụng [Trang GitLab](https://pages.gitlab.io/) khi bạn đang ở đó.

* [static](https://helpex.vn/it-code/cau-hoi-chu-de/static)
* [dynamic](https://helpex.vn/it-code/cau-hoi-chu-de/dynamic)
* [ssg](https://helpex.vn/it-code/cau-hoi-chu-de/ssg)
* [static site generator](https://helpex.vn/it-code/cau-hoi-chu-de/static-site-generator)
* [gitlab](https://helpex.vn/it-code/cau-hoi-chu-de/gitlab)

19 hữu ích0 bình luận3.3k xemchia sẻ

# [Tạo danh sách bài viết với IBM WCM 8.0 (Phần 4)](https://helpex.vn/article/tao-danh-sach-bai-viet-voi-ibm-wcm-8.0-phan-4-60c99d993f07bf0a5af5b7d8)

![Hoàng Quang Thiên](https://cdn.helpex.vn/upload/2015/08/28/55ee42fe8b75f32e34150d88-091821536_50x50.jpg)

[Hoàng Quang Thiên](https://helpex.vn/thanh-vien/55ee42fe8b75f32e34150d88)·17:00 27/06/2016

5 ngày trước

Trong Phần 1 , 2 và 3 , chúng tôi đã tạo các khối xây dựng thư viện, bài báo và danh sách bài viết. Trong Phần 4, chúng tôi sẽ thêm các bước cuối cùng trước khi thêm mọi thứ vào các trang Cổng thông tin của chúng tôi trong Phần 5.

## Thành phần công cụ tác giả

Để cho phép tác giả của nội dung WCM tạo, chỉnh sửa hoặc xóa nội dung WCM trực tiếp trên trang web (trái ngược với việc tạo thông qua ứng dụng Quản lý nội dung web), WCM cung cấp thành phần Công cụ tác giả. Thành phần này khởi chạy một portlet Authoring độc lập trong cửa sổ bật lên hoặc bằng cách chuyển hướng người dùng đến một trang ẩn đặc biệt.

Đối với nhu cầu của chúng tôi, chúng tôi sẽ tạo ra hai thành phần công cụ tác giả: một để tạo một bài báo mới và một để chỉnh sửa và xóa các bài viết riêng lẻ. Đầu tiên sẽ chỉ được hiển thị một lần (gần đầu danh sách bài viết), trong khi cái thứ hai sẽ được hiển thị trên mỗi bài viết.

## Bước 1: Tạo công cụ sáng tác "Bài viết mới"

Trong thư viện "bài viết-danh sách-thiết kế", hãy tạo một thành phần Công cụ tác giả mới.

Cung cấp tên và tiêu đề hiển thị.

Đối với thiết kế "Hành động mới", hãy cung cấp HTML để hiển thị liên kết để mở cửa sổ bật lên công cụ tác giả. Điều này được thực hiện bằng cách sử dụng thẻ Giữ chỗ:

*<a href=\[Placeholder tag='href'][>… </a>*

Đặt “Mẫu tác giả” thành “Đã chọn” và đặt Mẫu tác giả đã chọn thành Mẫu tác giả bài viết.

Đặt giá trị “Khu vực trang web” thành “Đã chọn” và đặt “Khu vực trang web được chọn” thành khu vực trang Bài viết của chúng tôi trong thư viện nội dung. Điều này đảm bảo mục nội dung đã tạo được tạo trong khu vực trang web được sử dụng bởi thành phần menu của chúng tôi.

Trong "Tùy chọn bản trình bày":

1. Cung cấp HTML tiêu đề sẽ bao bọc thẻ liên kết của chúng tôi;
2. Cung cấp chân trang để đóng HTML.

Bây giờ bạn sẽ có một cái gì đó như thế này: 

![Tạo danh sách bài viết với IBM WCM 8.0 (Phần 4)](https://cdn.helpex.vn/upload/2016/06/27/05-00-00-000-de60c110-cedd-4bdf-9293-94971e050a2a.jpg)

Lưu và đóng.

Bạn có thể tìm thấy phần đánh dấu ở trên trong ["article_list_listing_5.html" trong phần chính](https://gist.github.com/roanbester/b30ab3a7c9553a504576e7fbe39b4cf9#file-article_list_listing_5-html) .

#### Ghi chú

Tác giả (trình chỉnh sửa WCM) có thể thay đổi vị trí cho mục nội dung mới trên mẫu tác giả theo mặc định. Thường thì điều này không được mong muốn; bạn có thể ẩn khả năng này khỏi mẫu tác giả (ngoài phạm vi).



## Bước 2: Tạo công cụ tác giả "Chỉnh sửa bài viết"

Trong thư viện "bài viết-danh sách-thiết kế", hãy tạo một thành phần Công cụ tác giả mới.

Cung cấp tên và chức danh.

Trong “Thuộc tính hành động mới”, hãy đặt mẫu Tác giả thành “Tự động điền”.

Trong “Khu vực trang web đã chọn”, hãy đặt Khu vực trang web thành “Tự động điền”.

Trong “Chỉnh sửa thuộc tính hành động”, hãy đặt “Đang chỉnh sửa” thành “Chỉnh sửa nội dung trực tiếp” và thêm đánh dấu cho các thiết kế hành động Chỉnh sửa và Xóa. Đánh dấu có thể được tìm thấy trong ["article_list_listing_6.html" trong ý chính](https://gist.github.com/roanbester/b30ab3a7c9553a504576e7fbe39b4cf9#file-article_list_listing_6-html) .

Thêm đánh dấu bên dưới Tùy chọn trình bày để hiển thị đầu trang và chân trang của các công cụ tác giả.

Lưu và đóng.

## Bước 3: Thêm công cụ tác giả vào thiết kế

Bây giờ chúng ta đã có các công cụ soạn thảo, chúng ta có thể thêm chúng vào thành phần trình bày danh sách (đối với danh sách bài viết) và mẫu trình bày Bài viết.

### Bài báo mới

Để thêm thành phần công cụ tác giả Bài viết mới, hãy chỉnh sửa thành phần Trình bày danh sách cho danh sách bài viết của chúng tôi. Trong “Đánh dấu bản trình bày danh sách”, hãy nhấp vào “Chèn thẻ” cho phần Tiêu đề để nhập thành phần công cụ tác giả. Kết quả là một thẻ như thế này:

*\[Tên thành phần = "article-list-design / article list / atools - new article"]*

### Chỉnh sửa bài viết

Chúng tôi cần thêm các công cụ tác giả để chỉnh sửa và xóa một bài báo trong cả Bản trình bày danh sách cũng như trên chế độ xem chi tiết bài viết.

Đối với Bản trình bày danh sách, trong phần “Thiết kế kết quả 1”, hãy thực hiện tương tự, thêm thành phần công cụ soạn thảo Bài viết. Hãy chú ý đặt thuộc tính “compute” thành “always”, để cho phép công cụ tác giả chọn mục nội dung hiện tại. Kết quả là một thẻ thành phần như thế này:

*\[Tên thành phần = "article-list-design / article list / atools - article edit" compute = "always"]*

## Bước 4: Tạo kiểu

Để kết thúc danh sách bài viết, chúng tôi cần thêm một lượng nhỏ kiểu dáng để sửa chữa các công cụ tạo tác giả và hình ảnh nhỏ như đường ngang. Cách tốt nhất để làm điều này là tạo Thành phần CSS và thêm thành phần này vào các mẫu bản trình bày có liên quan.

Tạo tệp .css mới trên máy tính của bạn bằng trình chỉnh sửa yêu thích của bạn. Bạn có thể sử dụng ["article_list.css" từ ý chính](https://gist.github.com/roanbester/b30ab3a7c9553a504576e7fbe39b4cf9#file-article_list-css) nếu bạn đang sử dụng bootstrap hoặc để xem các chỉnh sửa về kiểu dáng mà tôi đã thực hiện.

Trong WCM, hãy chuyển đến thư viện "article-list-design" và tạo Thành phần CSS mới.

Cung cấp tên và tiêu đề hiển thị.

Tải lên tệp CSS bạn vừa tạo.

Đặt Loại là “Biểu định kiểu liên tục” để đảm bảo CSS luôn được tải lên trang.

Đặt loại phương tiện thành “Tất cả”, vì chúng tôi sẽ sử dụng tệp này cho tất cả các loại phương tiện. Ví dụ: bạn có thể thêm ghi đè CSS vào một trang cho một loại phương tiện cụ thể, ví dụ: cho thiết bị in hoặc thiết bị di động.

Lưu và đóng.

Bây giờ bạn sẽ có cái này:

![Tạo danh sách bài viết với IBM WCM 8.0 (Phần 4)](https://cdn.helpex.vn/upload/2016/06/27/05-00-00-000-49e80b06-bc57-4ac2-85f9-2f13f5fe343d.jpg)

Thêm thành phần CSS vào cả hai mẫu bản trình bày mà chúng tôi đã tạo cho đến nay (một cho bài viết và một cho thành phần danh sách / menu). Bạn có thể xem ["article_listing_7.html" trong ý](https://gist.github.com/roanbester/b30ab3a7c9553a504576e7fbe39b4cf9#file-article_list_listing_7-html)  chính để biết mẫu bản trình bày Thành phần mẫu và ["article_listing_1.html"](https://gist.github.com/roanbester/b30ab3a7c9553a504576e7fbe39b4cf9#file-article_list_listing_1-html) cho mẫu bản trình bày Bài viết.

## Tóm lược

Trong phần này, chúng tôi đã thêm các công cụ tác giả cần thiết để tạo, chỉnh sửa và xóa bài viết, cũng như một số chỉnh sửa kiểu cơ bản đối với giao diện của danh sách bài viết và chế độ xem chi tiết.

Điều này kết thúc việc tạo ra tất cả nội dung WCM; tất cả những gì còn lại bây giờ là hiển thị nó trên các trang Cổng thông tin và đảm bảo rằng các liên kết được nhấp vào trang danh sách bài viết sẽ chuyển đến trang chi tiết để hiển thị bài báo đã chọn. Điều này sẽ được xử lý trong Phần 5.

* [ibm](https://helpex.vn/it-code/cau-hoi-chu-de/ibm)
* [websphere](https://helpex.vn/it-code/cau-hoi-chu-de/websphere)
* [content-management-system](https://helpex.vn/it-code/cau-hoi-chu-de/content-management-system)

9 hữu ích0 bình luận3.0k xemchia sẻ

# [Sử dụng log với Angular 1.5](https://helpex.vn/article/su-dung-log-voi-angular-1.5-60c999663f07bf0a5af5b79c)

![Huỳnh Hòa Hiệp](https://cdn.helpex.vn/upload/2020/08/22/55ee430a8b75f32e34151b41-062658544_50x50.jpg)

[Huỳnh Hòa Hiệp](https://helpex.vn/thanh-vien/55ee430a8b75f32e34151b41)·17:00 26/07/2016

13 giờ trước

*(Bài viết giả định ít nhất bạn có kiến ​​thức cơ bản về Angular. Angular là một framework rất kiên định, vì vậy hãy đảm bảo bạn có một số kinh nghiệm với Angular trước khi làm theo các hướng dẫn được trình bày bên dưới.)*

Các bản ghi có thể tích hợp vào bất kỳ khuôn khổ Javascript nào bạn muốn sử dụng. Trước đây, chúng tôi đã kiểm tra việc thêm [Logentries vào một ứng dụng React](https://blog.logentries.com/2016/05/integrating-the-logentries-javascript-library-with-react/) . Bài đăng này sẽ minh họa cách thêm Thông tin đăng nhập vào ứng dụng Angular v1 của bạn bằng cách sử dụng Nhà cung cấp. Kiến trúc Nhà cung cấp của Angular v1 cung cấp một cách mô-đun và mạnh mẽ để thêm chức năng vào các ứng dụng Angular của bạn.

Kiến trúc Angular Provider là một trong những thiết bị tuyệt vời của Angular v1. Tài liệu dành cho Nhà cung cấp có [tại đây](https://docs.angularjs.org/guide/providers) . Trình cung cấp là các đối tượng độc lập được đưa vào và sử dụng bên trong các ứng dụng Angular. Chúng là các khối xây dựng của hầu hết các ứng dụng Angular và thực thi một cấu trúc mô-đun thúc đẩy việc tái sử dụng và làm sạch mã. Có một số loại Nhà cung cấp; chúng ta sẽ sử dụng loại Factory.

Angular Factory là một đối tượng tùy chỉnh được tạo bằng phương pháp Angular factory. Chuyển một nhà máy vào mô-đun Angular của bạn thông qua quá trình tiêm sẽ làm cho đối tượng tùy chỉnh của bạn có thể truy cập bên trong mô-đun. Thông thường, Factory được sử dụng để tạo một đối tượng chỉ được tạo một lần và trả về một đối tượng được chia sẻ. Dịch vụ phía máy khách Logentries rất phù hợp với mẫu Factory vì nó cũng hoạt động như một tài nguyên được chia sẻ. Phần lớn mã được sử dụng trong nhà máy là để khởi tạo đối tượng Logentries. Sau khi khởi tạo, Factory sẽ hiển thị đối tượng Logentries.

Hãy bắt đầu bằng cách xem index.html:

```

```

Thẻ ng-app xác định mô-đun chính mà Angular đang tải vào phần thân. LeAngularSample là mô-đun mẫu đang được sử dụng để minh họa thư viện. LogEntriesFactory.js giới thiệu thư viện Logentries. Mã trong app.js chèn và sử dụng mã Logentries, đồng thời chèn thành phần giao diện người dùng của mẫu vào thẻ “<selection>” tùy chỉnh. Các thẻ còn lại bổ sung các thư viện javascript cần thiết.

Index.html là trang mở đầu. Hãy xem các tệp script đang được nhập, bắt đầu với tệp LogEntriesFactory.js:

```

```

Mã bắt đầu bằng cách tạo một mô-đun Angular mới có tên là “LogEntries”. Mô-đun này là một mô-đun Angular độc lập có khả năng được sử dụng ở mọi nơi. Tệp này có thể được gỡ bỏ từ ứng dụng này và được chèn vào bất kỳ ứng dụng nào.

Mô-đun tạo một đối tượng được gọi là LoggerFactory. LoggerFactory được sử dụng trong mã để tương tác với đối tượng Logentries. LoggerFactory khởi động, đặt mã thông báo Logentries, khởi tạo đối tượng trên mỗi tài liệu Logentries và trả về đối tượng Logentries đã chuẩn bị.

Tệp script khác chứa chỉ thị. Chỉ thị trông như thế này:

```

```

 Chỉ thị là cơ chế của Angular để tạo các phần tử giao diện người dùng. Chỉ thị của chúng tôi thay thế thẻ <selection> bằng nội dung của HTML trong tệp template.html (được hiển thị bên dưới). Các đoạn mã thú vị nhất cho mục đích của chúng tôi là:

* **Injector** - angle.module ('LeAngularSample', [ *'LogEntries'* ]) LogEntries là tên của mô-đun có chứa LoggerFactory. Dòng này yêu cầu Angular đưa mô-đun LogEntries vào mô-đun LeAngularSample và làm cho các thành phần của mô-đun LogEntries có thể truy cập được.
* **templateUrl -** templateUrl: 'template.html'Angular thay thế thẻ lựa chọn bằng nội dung của tệp mẫu tại templateUrl
* **controller** - controller: function ($ scope, LoggerFactory) {Bộ điều khiển bao gồm mã được gọi bởi các thành viên của chỉ thị lựa chọn. Lưu ý rằng các chức năng trong bộ điều khiển được gọi trong ng-click của mẫu. Mỗi liên kết từ mẫu sẽ gọi chức năng đối ứng của nó từ bộ điều khiển. LoggerFactory có thể được bao gồm vì mô-đun đã được đưa vào ở trên. Nó nằm trong các tham số chức năng của bộ điều khiển nên nó có thể được sử dụng trong mã của bộ điều khiển.

Tệp html mẫu trông như thế này (với một số văn bản đã bị xóa):

```

```

Lưu ý bốn dòng với ng-click. Các lệnh ng-click được hiển thị dưới dạng các sự kiện nhấp chuột. Bốn chức năng tương ứng trực tiếp với các phương thức được gọi trong mã bộ điều khiển của chỉ thị. Angular sẽ tự động liên kết các chức năng trong ng-click với chỉ thị.

Mẫu đi kèm với một thiết lập máy chủ nút để hiển thị trang. README có hướng dẫn cách bắt đầu. Sau khi thiết lập và chạy, trang sẽ giống như hình dưới đây. Sử dụng bất kỳ liên kết nào trong số này sẽ gửi nhật ký đến tài khoản Logentries của bạn với loại tương ứng.

Ràng buộc Logentries vào mã Angular của bạn cũng đơn giản như việc đưa vào một mô-đun. Hãy sử dụng LogEntriesFactory.js và sửa đổi nó để hoạt động trong ứng dụng Angular của bạn. Việc đưa thư viện phía máy khách Logentries vào mã của bạn thật dễ dàng nhờ vào các thành phần mô-đun và chèn của Angular.

Bạn có thể tìm thấy repo GitHub với đầy đủ mẫu tại  <https://github.com/LogentriesCommunity/Logentries-Angular-Sample>

* [angular](https://helpex.vn/it-code/cau-hoi-chu-de/angular)
* [logentries](https://helpex.vn/it-code/cau-hoi-chu-de/logentries)
* [code](https://helpex.vn/it-code/cau-hoi-chu-de/code)
* [integration](https://helpex.vn/it-code/cau-hoi-chu-de/integration)
* [web dev](https://helpex.vn/it-code/cau-hoi-chu-de/web-dev)

9 hữu ích0 bình luận5.7k xemchia sẻ

# [Làm cho các khái niệm và thông số kỹ thuật web được trình bày dưới dạng Trợ giúp thời gian thực trong thiết kế API ...](https://helpex.vn/article/lam-cho-cac-khai-niem-va-thong-so-ky-thuat-web-duoc-trinh-bay-duoi-dang-tro-giup-thoi-gian-thuc-trong-thiet-ke-api-...-60c9903a3f07bf0a5af5b71e)

![Đặng Hải Ðăng](https://cdn.helpex.vn/upload/2016/05/23/55ee433b8b75f32e341558c7-114950728_50x50.jpg)

[Đặng Hải Ðăng](https://helpex.vn/thanh-vien/55ee433b8b75f32e341558c7)·17:00 05/09/2016

hôm qua

Tôi đã lấy [kho lưu trữ GitHub](https://github.com/dret/webconcepts) cho hoạt động của [Khái niệm web](http://webconcepts.info/) ( [@dret](https://twitter.com/dret) ) của Erik Wilde và phân nhánh nó, sau đó tạo một số JSON mà tôi có thể sử dụng để nhập vào hệ thống giám sát API của mình. Tôi đã thêm thông số kỹ thuật vào hệ thống lập lịch Tweet và LinkedIn của mình theo cách thủ công, nhưng tôi vẫn quên quay lại trang web và thêm các mục khác. Vì vậy, tôi muốn tiếp tục và nhập tất cả các khái niệm và thông số kỹ thuật, đồng thời lên lịch cho các bài đăng trên Twitter và LinkedIn cho mọi thứ, trong vài tháng tới.[](http://webconcepts.info/)

[Đầu tiên, tôi tạo JSON cho các khái niệm, sau đó tôi tạo JSON cho các thông số kỹ thuật, bạn có thể xem ở đây.](http://apievangelist.com/2016/09/01/making-web-concepts-and-specs-present-as-real-time-help-in-api-design-tooling/)

Tôi đã bỏ qua các mối quan hệ giữa các khái niệm và thông số kỹ thuật, vì tôi sẽ chỉ liên kết đến Các khái niệm web và để mọi người tự khám phá. Khi tôi xem qua JSON, tôi nghĩ về lý do tại sao những khái niệm và thông số kỹ thuật này không có sẵn trong công cụ thiết kế API dưới dạng trợ giúp và chú giải công cụ, để các nhà thiết kế và kiến ​​trúc sư API có thể học hỏi từ chúng và được nhắc nhở trong thời gian thực — tạo ra các API của họ. 

Có vẻ như cần có tính năng tự động hoàn thành cho các trường tiêu đề HTTP, mã trạng thái HTTP và các mục liên quan khác nếu cần. Có rất nhiều kiến ​​thức về web trong công việc của Erik, và thông qua các khái niệm và thông số kỹ thuật web mà anh ấy đã sắp xếp, có vẻ như chúng sẽ có sẵn theo mặc định trong các dịch vụ và công cụ thiết kế API, và bắt đầu được đưa vào các IDE như Atom, Eclipse, và Visual Studio. Có lẽ họ đã có, và tôi chỉ không biết.

* [api](https://helpex.vn/it-code/cau-hoi-chu-de/api)
* [web dev](https://helpex.vn/it-code/cau-hoi-chu-de/web-dev)

0 hữu ích0 bình luận3.8k xemchia sẻ

# [Đánh giá về tính bất biến trong Ruby](https://helpex.vn/article/danh-gia-ve-tinh-bat-bien-trong-ruby-60c98e623f07bf0a5af5b701)

![Huỳnh Mỹ Tâm](https://cdn.helpex.vn/upload/2016/01/02/55ee43088b75f32e341518e8-083934015_50x50.jpg)

[Huỳnh Mỹ Tâm](https://helpex.vn/thanh-vien/55ee43088b75f32e341518e8)·17:00 13/09/2016

14 giờ trước

Trạng thái có thể thay đổi được chia sẻ là nguồn gốc của rất nhiều lỗi. Khi hai hoặc nhiều đối tượng sử dụng cùng một phần dữ liệu có thể thay đổi, tất cả chúng đều có khả năng phá vỡ lẫn nhau theo những cách khó có thể gỡ lỗi. Tuy nhiên, nếu dữ liệu được chia sẻ là bất biến, các đối tượng này không thể ảnh hưởng lẫn nhau và được tách rời một cách hiệu quả.

Bài viết này là một đánh giá về các tùy chọn có sẵn cho Rubyists liên quan đến tính bất biến. Chúng ta sẽ xem xét các tính năng tích hợp của Ruby 2.3 và một vài viên ngọc.

## Cấp đông Lib tiêu chuẩn

Hãy bắt đầu với `freeze`phương thức từ thư viện chuẩn:

### Đối tượng # đóng băng

Ngăn chặn các sửa đổi thêm đối với `obj`. A `RuntimeError`sẽ được nâng lên nếu cố gắng sửa đổi. Không có cách nào để giải phóng một đối tượng bị đóng băng. Xem thêm `Object#frozen?`.

Phương thức này trả về tự.

```

```

sản xuất:

```

```

Đối tượng của các lớp sau đây luôn đông lạnh: `Fixnum`, `Bignum`, `Float`, `Symbol`.

Các `freeze`phương pháp sẽ làm việc cho hầu hết các đối tượng, trong đó có trường hợp của các tầng lớp người dùng định nghĩa:

```

```

Ngoại lệ duy nhất là các lớp kế thừa từ `BasicObject`. Các `freeze`phương pháp được định nghĩa trên `Object`, vì vậy nó không phải là có sẵn với các trường hợp `BasicObject`:

```

```

Bạn sẽ thường thấy `freeze`được sử dụng khi gán hằng số, để đảm bảo rằng các giá trị không thể bị thay đổi. Điều này là do việc gán lại một biến hằng số sẽ tạo ra một cảnh báo, nhưng việc thay đổi một giá trị hằng số thì *không* .

```

```

Vì vậy, nếu bạn muốn đảm bảo rằng các hằng số của bạn thực sự không đổi, bạn cần cố định giá trị:

```

```

Vấn đề chính của `freeze`phương pháp là nó *nông* , trái ngược với đệ quy. Ví dụ: một mảng cố định không thể có thêm, xóa hoặc thay thế các phần tử, nhưng bản thân các phần tử hiện tại vẫn có thể thay đổi:

```

```

## Frozen String Literals Trong Ruby 2.3

Bạn có thể nhận thấy rằng các biểu tượng và số được tự động đóng băng trong Ruby. Ví dụ, không thể thực hiện `add!`phương pháp này :

```

```

Trong hầu hết các ngôn ngữ, ký tự chuỗi cũng không thay đổi, giống như số và ký hiệu. Tuy nhiên, trong Ruby, tất cả các chuỗi đều có thể thay đổi theo mặc định.

Điều này sẽ thay đổi trong phiên bản chính tiếp theo của Ruby. Tất cả các ký tự chuỗi sẽ không thay đổi theo mặc định trong Ruby 3, nhưng điều đó vẫn còn vài năm nữa. Trong thời gian chờ đợi, chức năng này có thể được kích hoạt tùy chọn kể từ Ruby 2.3.

Có một tùy chọn dòng lệnh có sẵn cho phép các ký tự chuỗi cố định trên toàn cầu:

```

```

Thật không may, điều này sẽ phá vỡ rất nhiều mã và đá quý đã tồn tại trước đó, bởi vì hầu hết mã được viết với giả định rằng các ký tự chuỗi có thể thay đổi được.

Cho đến khi mã cũ hơn được cập nhật để xử lý các chuỗi bị cố định, tốt hơn nên bật tùy chọn này trên cơ sở từng tệp bằng cách sử dụng “nhận xét kỳ diệu” này ở đầu mỗi tệp:

```

```

Khi nhận xét kỳ diệu này tồn tại, chuỗi ký tự bên trong tệp sẽ bị đóng băng theo mặc định, nhưng mã trong các tệp khác sẽ không bị ảnh hưởng.

Khi bạn thực sự muốn một chuỗi có thể thay đổi, bạn phải tạo một `String#new`chuỗi bằng hoặc sao chép một chuỗi cố định bằng cách sử dụng `String#dup`:

```

```

## Các `ice_nine`Gem - Freezing Recursive

Nó chỉ ra rằng việc đóng băng một cách đệ quy một đối tượng đúng cách là một chút khó khăn, nhưng may mắn thay có một viên ngọc quý cho điều đó. Các [`ice_nine`đá quý](https://github.com/dkubb/ice_nine) áp dụng `freeze`phương pháp đệ quy, đảm bảo rằng một đối tượng là thực sự đông lạnh:

```

```

Đá quý cũng cung cấp một phần mở rộng cốt lõi tùy chọn để xác định `Object#deep_freeze`, để thuận tiện:

```

```

## Các `values`Gem - Các lớp Immutable Struct-Like

Thay vì đóng băng các đối tượng có thể thay đổi, thường tốt hơn là tạo các đối tượng không thể thay đổi theo mặc định. Đây là nơi mà [`values`đá quý](https://github.com/tcrayford/values) rất hữu ích.

Nếu bạn đã quen thuộc với [`Struct`thư viện tiêu chuẩn](http://ruby-doc.org/core-2.3.0/Struct.html) , `values`thì về cơ bản gem cũng giống như vậy, ngoại trừ việc nó là bất biến theo mặc định.

Đây là một số mã ví dụ:

```

```

Cũng giống như `Struct`các lớp, các `Value`lớp này có thể có các phương thức tùy chỉnh:

```

```

Không giống như `Struct`các lớp, các lớp này sẽ tạo ra lỗi nếu thiếu bất kỳ thuộc tính nào khi tạo. Đây là một điều tốt, vì nó cảnh báo bạn về những lỗi tiềm ẩn thay vì im lặng bỏ qua chúng.

```

```

Các lớp này chỉ là bất biến nông, giống như `freeze`phương thức tích hợp sẵn. Bản thân các đối tượng không thể thay đổi, nhưng các thuộc tính của chúng vẫn có thể thay đổi được.

```

```

Toàn bộ viên ngọc chỉ có khoảng [100 dòng mã](https://github.com/tcrayford/Values/blob/b3b57abd344806f32b15126a40551414ebd4a01b/lib/values.rb) , vì vậy rất dễ hiểu về toàn bộ.

Đối với phần lớn các tình huống mà bạn sẽ sử dụng `Struct`, tôi nghĩ `Value`các lớp học là lựa chọn tốt hơn. Đối với những tình huống hiếm hoi mà bạn đang cố gắng đạt được từng giọt hiệu suất cuối cùng, `Struct`vẫn là lựa chọn tốt hơn, ít nhất là trên MRI. Điều đó không có nghĩa là `Value`các lớp chậm - chúng có hiệu suất tương tự như bất kỳ lớp Ruby nào khác, nếu không muốn nói là tốt hơn do quá trình băm tích cực. Trong MRI, `Struct`lớp được thực hiện theo một cách hiệu quả bất thường. Trong các triển khai khác, chẳng hạn như JRuby, có thể không có sự khác biệt về hiệu suất.

Nếu bạn không sử dụng `Struct`các lớp, bạn có thể tự hỏi tại sao và nơi bạn muốn sử dụng một trong hai lớp đó. Nguồn tốt nhất mà tôi có thể chỉ cho bạn là [Giá trị của các Giá trị của Rich Hickey](https://www.infoq.com/presentations/Value-Values) . Cuối cùng, nó tóm tắt tất cả những lợi ích của *ngữ nghĩa giá trị* , mà Rich giải thích chi tiết.

## Các `adamantium`Gem - Tự động Recursive Freezing

Các [`adamantium`đá quý](https://github.com/dkubb/adamantium) cung cấp đóng băng đệ quy tự động cho các lớp học của Ruby qua `ice_nine`đá quý.

```

```

Adamantium hoạt động bằng cách ghi đè `new`phương thức lớp. Sau khi một đối tượng đã được cấp phát và `initialize`phương thức của nó đã được chạy, nó sẽ bị đóng băng bằng cách sử dụng `ice_nine`gem. Điều này có nghĩa là bạn có thể thay đổi đối tượng từ bên trong `initialize`, nhưng không bao giờ lặp lại.

Để tạo các đối tượng bất biến mới từ những đối tượng hiện có, có một `transform`phương pháp. Điều này hoạt động bằng cách tạo ra một bản sao có thể biến đổi, chạy một khối đột biến trên bản sao, sau đó đóng băng sâu bản sao đó trước khi trả lại. Bạn có thể xem một ví dụ về điều này trong `with_name`phương pháp trên.

Adamantium yêu cầu nhiều tấm boilerplate hơn `values`gem, nhưng nó thực hiện đóng băng đệ quy thích hợp. Nó cũng có chức năng tự động ghi nhớ và đóng băng các giá trị trả về của các phương thức.

## Các `anima`Gem - includable Value Semantics

Các [`anima`viên ngọc](https://github.com/mbj/anima) cơ bản là một hỗn hợp của `values`đá quý và `adamantium`đá quý.

```

```

Nó có tính ngắn gọn của `values`đá quý và sử dụng Adamantium để đóng băng đệ quy tự động.

Hãy coi đây là phiên bản có trọng lượng nặng của `values`viên đá quý. Nó có một vài tính năng hơn, nhưng nó cũng mang lại lăm đá quý như phụ thuộc: `ice_nine`, `memoizable`, `abstract_type`, `adamantium`và `equalizer`. Để so sánh, `values`gem không có phụ thuộc và được triển khai trong một tệp duy nhất với khoảng 100 dòng mã.

## Các `hamster`Gem - Persistent Cấu trúc dữ liệu

Các [`hamster`đá quý](https://github.com/hamstergem/hamster) cung cấp một tập các lớp cấu trúc dữ liệu liên tục. Các lớp học này thay thế bất biến cho các lớp học của Ruby tiêu chuẩn như `Hash`, `Array`, và `Set`. Chúng hoạt động theo kiểu tương tự như các viên ngọc khác - không thể sửa đổi các đối tượng, nhưng bạn có thể tạo các đối tượng mới dựa trên các đối tượng hiện có.

Làm việc với các giá trị không thay đổi thường đòi hỏi nhiều bản sao, giống như sao chép toàn bộ mảng chỉ để thêm một phần tử mới. Cấu trúc dữ liệu liên tục cung cấp hiệu suất tốt hơn cho các loại hoạt động này bằng cách giảm số lượng đối tượng cần được sao chép và sử dụng lại càng nhiều đối tượng càng tốt.

Ví dụ, nếu bạn muốn tạo một mảng được cố định từ một mảng đã được cố định hiện có, bạn sẽ phải làm như thế này trong Ruby đơn giản:

```

```

Với `Hamster::Vector`, điều này sẽ trông giống như:

```

```

Trong `Hamster::Vector`phiên bản, `new_one`có thể không phải là một bản sao hoàn toàn của `original`. Bên trong, `new_one`giá trị có thể chỉ giữ `4`một tham chiếu cộng với `original`. Chia sẻ trạng thái bên trong theo cách này cải thiện cả tốc độ và mức sử dụng bộ nhớ, đặc biệt là đối với các đối tượng lớn. Tất cả điều này diễn ra tự động dưới mui xe, vì vậy bạn không cần phải suy nghĩ về nó.

Để có cái nhìn tổng quan về chủ đề này, tôi giới thiệu một bài nói chuyện Rich Hickey khác: [Cấu trúc dữ liệu liên tục và tài liệu tham khảo được quản lý](https://www.infoq.com/presentations/Value-Identity-State-Rich-Hickey) . Chuyển tiếp đến 23:49 để đến phần cụ thể về cấu trúc dữ liệu liên tục.

## Đối tượng giá trị Virtus

Tôi muốn nhanh chóng đề cập đến [`virtus`đá quý](http://www.rubypigeon.com/posts/a-review-of-immutability-in-ruby/) , mặc dù tôi khuyên không nên sử dụng nó. Nó có một số chức năng "đối tượng giá trị" hoạt động rất giống với `values`and `anima`gems, nhưng với các tính năng bổ sung xung quanh xác thực kiểu và cưỡng chế.

```

```

Về lý do tại sao tôi khuyên bạn không nên sử dụng nó, hãy để tôi trích dẫn tác giả của viên đá quý Piotr Solnica trong [chủ đề reddit này](https://www.reddit.com/r/ruby/comments/3sjb24/virtus_to_be_abandoned_by_its_creator/) :

Lý do tại sao tôi không còn quan tâm đến việc làm việc trên nền tảng công nghệ không phải là điều tôi có thể giải thích dễ dàng, nhưng tôi sẽ cố gắng.

\[…]

\[Nó] đã được tối ưu hóa cho một trường hợp sử dụng cụ thể là lưu trữ dữ liệu từ một biểu mẫu web để làm cho cuộc sống của chúng ta đơn giản hơn và chức năng này chỉ đơn giản là được đưa vào ORM

\[…]

Tôi đã phạm phải một sai lầm mà trước đây đã từng mắc phải từ ActiveRecord.

\[…]

Tôi đã mất một lúc để hiểu điều gì đang thực sự diễn ra. Virtus là viên ngọc mang lại di sản của DataMapper, mang lại di sản của… ActiveRecord. Đó là một quá trình dài để hiểu một số vấn đề cơ bản, khi tôi đã hiểu chúng, tôi bắt đầu làm việc trên các thư viện mới để giải quyết những vấn đề đó theo cách tốt hơn. Tôi càng làm việc nhiều hơn với những thư viện đó, tôi càng thấy rõ ràng rằng Virtus sẽ phải được thay đổi hoàn toàn và sẽ không còn phục vụ cùng mục đích nếu tôi muốn xây dựng nó theo cách mà tôi nghĩ là đúng.

Virtus đã cố gắng trở thành một con dao quân đội Thụy Sĩ phổ biến cho các cuộc cưỡng chế, như một hệ quả tự nhiên của việc được trích xuất từ ​​một ORM có nhiều điểm chung với ActiveRecord, nó đã cố gắng làm quá nhiều, với rất nhiều hành vi ngầm, các trường hợp cạnh kỳ lạ, hiệu suất các vấn đề và DSL phức tạp.

\[…]

Hơn nữa, thuộc tính DSL với nhiều tùy chọn là một mô hình chống. Đó là những gì tôi đã học được theo thời gian. Và nó không kết thúc ở đây - thiếu an toàn kiểu thực tế là một vấn đề, Virtus có một chế độ nghiêm ngặt nhưng không thể làm cho nó đúng trong một thư viện được sử dụng trong nhiều bối cảnh khác nhau.

## Sắp tới tiếp theo: Phong cách kỷ luật và chức năng

Bài viết này chỉ đề cập đến các tùy chọn thuộc loại nặng tay. Tất cả đều yêu cầu đá quý hoặc mã bổ sung.

Bài tiếp theo sẽ nói về cái mà tôi gọi là “phong cách chức năng” - sử dụng kỷ luật để tránh đột biến, thay vì thực thi tính bất biến. Nó không yêu cầu thêm đá quý và không cần thêm mã. Giữ nguyên!

* [ruby](https://helpex.vn/it-code/cau-hoi-chu-de/ruby)
* [code](https://helpex.vn/it-code/cau-hoi-chu-de/code)
* [web dev](https://helpex.vn/it-code/cau-hoi-chu-de/web-dev)
* [immutable](https://helpex.vn/it-code/cau-hoi-chu-de/immutable)
* [example](https://helpex.vn/it-code/cau-hoi-chu-de/example)

5 hữu ích0 bình luận4.1k xemchia sẻ

# [Chuẩn bị Hộp công cụ của bạn cho Khuôn khổ Sharepoint](https://helpex.vn/article/chuan-bi-hop-cong-cu-cua-ban-cho-khuon-kho-sharepoint-60c98ccc3f07bf0a5af5b6e3)

![Đặng Hướng Thiện](https://cdn.helpex.vn/upload/2019/08/19/55ee433b8b75f32e34155929-040323564_50x50.jpg)

[Đặng Hướng Thiện](https://helpex.vn/thanh-vien/55ee433b8b75f32e34155929)·17:00 22/09/2016

15 giờ trước

Với SharePoint Framework, các nhà phát triển có thể sử dụng các khung như Angular, WebPack & Kendo UI để thiết kế SharePoint UI tùy chỉnh. Tìm hiểu con đường bạn nên đi.\
\
Vào tháng bảy, chúng tôi đã ở một ngã ba. Chúng tôi vừa kết thúc một mô-đun SharePoint On-Premises mới với Angular v1.4 và ngOffice UI Fabric. Mô-đun trước đó của chúng tôi là Angular v1.2 với UI Bootstrap. Chúng tôi biết rằng SharePoint Framework sắp ra mắt và thậm chí cuối cùng sẽ được đưa xuống On-Premise vào năm 2017. Ngoài ra, với tốc độ JavaScript di chuyển, về cơ bản chúng tôi cần phải làm mới hộp công cụ của mình ba tháng một lần.

Đã đến lúc phải thực hiện một chút nghiên cứu — và vì vậy chúng tôi đã làm.

## Chọn một con đường

Nghiên cứu này đã đạt đến đỉnh cao trong việc viết [Sách chuẩn bị cho Hộp công cụ của bạn cho Khuôn khổ SharePoint với ](http://www.telerik.com/campaigns/kendo-ui/sharepoint-framework-ui-customization-angular)[Sách](https://github.com/johnnliu/contract-register) trắng về [giao diện người dùng Angular, Webpack và Kendo](http://www.telerik.com/campaigns/kendo-ui/sharepoint-framework-ui-customization-angular) , được xây dựng xung quanh [bản trình diễn Đăng ký Hợp đồng (GitHub) này](https://github.com/johnnliu/contract-register) . Các công nghệ chúng tôi chọn chủ yếu tập trung vào những gì chúng tôi đã quen thuộc, nhưng cũng những gì chúng tôi biết sẽ được hỗ trợ trong SharePoint Framework. Chúng tôi đã kiểm tra kỹ với các ví dụ từ nhiều chuyên gia đã viết blog về trải nghiệm [SharePoint Dev Kitchen](https://blog.mastykarz.nl/sharepoint-dev-kitchen/) của họ và đối chiếu với tất cả các [video PnP SPFx](https://www.youtube.com/channel/UC_mKdhw-V6CeCM7gTo_Iy7w) .

### Angular

Chúng tôi bắt đầu với Angular và [Kendo UI](http://www.telerik.com/kendo-ui/ui-for-office-365-sharepoint) bằng Gulp, nhưng quá trình xây dựng liên quan đến việc đóng gói vào CDN, vì vậy chúng tôi đã thêm WebPack.

Cuối cùng, thay vì nói chuyện trực tiếp với SharePoint hoặc sử dụng các thành phần Kendo UI DataSource (cũng hỗ trợ SharePoint REST), tôi muốn chúng tôi sử dụng [pnp-js-core](https://github.com/OfficeDev/PnP-JS-Core) — một API thông thạo để nói chuyện với điểm cuối REST từ nhóm Office PnP.

Chúng tôi đã chuyển phiên bản của mình lên [Angular v1.5](https://toddmotto.com/exploring-the-angular-1-5-component-method/) vì chúng tôi muốn ở vị trí tốt nhất để có thể "triển khai sản xuất" ngay hôm nay, nhưng vẫn ghi vào thông số kỹ thuật của thành phần sẽ là tiêu chuẩn trong Angular v2. Hơn nữa, SPFx-webparts sẽ chạy trong Ứng dụng di động SharePoint trong tương lai. Vì vậy, không cần phải làm thêm quá nhiều công việc một cách rõ ràng — chúng tôi đang xây dựng hướng tới tương lai nơi chúng tôi xây dựng và nó chạy trong trình duyệt và trên thiết bị di động.

### PnP JS Core

Đối với PnP JS Core, API thông thạo là một niềm vui khi làm việc cùng và cách thực hiện phân phối khá kỳ diệu. Trong v1.0.3, thư viện cũng bắt đầu hỗ trợ NodeJS, có nghĩa là bạn có thể sử dụng cùng một mã JavaScript để tương tác với SharePoint từ cả trình duyệt và máy chủ. Viết cùng một đoạn mã chạy ở cả hai nơi là chén thánh mà chúng ta luôn hướng tới. Nếu JavaScript có thể chạy ở mọi nơi, thì các thư viện chúng ta muốn sử dụng sẽ có thể chạy ở mọi nơi.

### WebPack

Khi chúng tôi tìm hiểu sâu hơn về điều kỳ diệu đó là [WebPack](https://github.com/webpack/webpack) , điều kỳ diệu của nó đã được hé mở. Trong [video](https://www.youtube.com/watch?v=rP8d_0MdedY) giới thiệu nhỏ này mà [chúng tôi đã quay cho Đăng ký hợp đồng](https://www.youtube.com/watch?v=rP8d_0MdedY) , bạn có thể nhận thấy WebPack đưa mã vào trình duyệt nhanh như thế nào — ứng dụng đã sẵn sàng trước khi thanh bộ Office 365 xuất hiện. Đây là một tác dụng phụ của việc tách mã. WebPack không chỉ đơn thuần liên hệ và hủy xác minh tệp JS, nó còn phóng các mô-đun JavaScript vào trình duyệt như một khẩu súng ngắn — tất cả cùng một lúc. WebPack gần như loại bỏ sự cần thiết của Gulp trong quá trình này. Gulp vẫn cần thiết để bắt đầu các tác vụ khác nhau, nhưng WebPack thực hiện công việc bên dưới và nó thực sự hoạt động tốt.

### TypeScript

Chúng tôi đã tranh luận rất nhiều về TypeScript. Nó sẽ làm cho IntelliSense và kiểm tra mã tốt hơn, nhưng chúng tôi quyết định loại bỏ nó. Đáng lẽ ra phải học thêm "một điều nữa", và danh sách đã dài ra. Hãy xem mã chúng tôi đã viết cho [sổ đăng ký hợp đồng](https://github.com/johnnliu/contract-register) (GitHub) và cho chúng tôi biết nếu chúng tôi đã lựa chọn đúng.

### Giao diện người dùng Kendo

Tôi cũng muốn nói về [Kendo UI](http://www.telerik.com/blogs/announcing-angular-kendo-ui) . Tôi đã không sử dụng Kendo UI trước dự án này. Đồng nghiệp của tôi và đồng tác giả của whitepaper này, Bart Bouwhuis, là một người hâm mộ lớn và anh ấy liên tục cho tôi thấy những đặc điểm thú vị. Sách trắng không phải là quảng cáo cho Tiến bộ (trước đây là Telerik), nhưng tôi cũng nghĩ rằng chúng ta không thực sự nói về giao diện người dùng Kendo nhiều như chúng ta nên làm.

Cảm giác của tôi là các thành phần Kendo UI đã thực sự trưởng thành — trong một số lĩnh vực cạnh tranh hoặc vượt quá UI Bootstrap.  Dễ dàng thêm các thành phần như  [Grid](http://demos.telerik.com/kendo-ui/grid/index) ,  [Window](http://demos.telerik.com/kendo-ui/window/index) và  [PDF export](http://demos.telerik.com/kendo-ui/grid/pdf-export) . Chúng đã hỗ trợ  [chủ đề Office 365](http://docs.telerik.com/kendo-ui/styles-and-layout/appearance-styling) , vì vậy chúng không có vẻ gì là lạc hậu.

Telerik hỗ trợ Angular v1 và họ vừa phát hành [bản xem trước dành cho nhà phát triển cho Angular 2](http://www.telerik.com/kendo-angular-ui/) . Cuối cùng, chúng tôi đã dành rất ít thời gian để làm cho các thành phần hoạt động với chúng tôi — trong hầu hết các trường hợp, chúng tôi đã tìm kiếm ví dụ trên [Telerik Docs](http://docs.telerik.com/kendo-ui/introduction) và nó chỉ hoạt động! Một điều may mắn nữa là chúng tôi không bao giờ cần phải chỉnh sửa CSS để khắc phục một số vấn đề về kiểu dáng. Đó thực sự là một vấn đề khá nhức nhối với UI Bootstrap hoặc ngOfficeUIFnai.

## Bản xem trước dành cho nhà phát triển SharePoint Framework (SPFx)

Mọi thứ đang chuyển động nhanh chóng. Bản xem trước dành cho nhà phát triển SPFx được đưa ra trong quá trình viết whitepaper. Nhớ chuyến tàu đó chứ? Hóa ra nó đến *rất* nhanh. Chúng tôi thích tốc độ chạy của nhóm SharePoint. Nhưng nó có nghĩa là chúng tôi có một số lưu ý để thêm vào.

Thứ nhất, whitepaper không chỉ về SPFx. Đó là về SharePoint như một nền tảng với AngularJS và WebPack, đồng thời có những phần đó sẵn sàng và được căn chỉnh cho SPFx. Đó là về một bộ công cụ cốt lõi ổn định hoạt động tốt cùng nhau. Đó là về một bộ công cụ chạy ngày nay trên SharePoint 2016, SharePoint 2013 và SharePoint Online. Bạn đã có thể sử dụng chúng mà không cần phải đợi SPFx.

Thứ hai, với SPFx thậm chí còn có nhiều cơ hội hơn. Chúng tôi sẽ hỗ trợ tốt hơn cho các chế độ Angular và SPA — hiện tại cả hai kịch bản đều chưa được phát hành. Vì vậy, câu chuyện sẽ phát triển và trở nên tuyệt vời hơn. Bản demo đăng ký hợp đồng có thể chạy ở chế độ phần mềm web SPFx — trong trường hợp đó, mã để khởi chạy ứng dụng và thiết lập các danh sách khác nhau sẽ đi vào bảng thuộc tính phần web. Chỉ người đóng góp mới có quyền truy cập vào việc tạo danh sách. 

Cách chúng tôi quyết định quản lý dòng chảy liên tục này là xuất bản bản cập nhật blog khi SPFx chính thức được phát hành để lấp đầy “khoảng trống” —các điều chưa biết về thời điểm xuất bản whitepaper. Vì vậy, hãy theo dõi bản cập nhật như vậy, có thể là sau Microsoft Ignite. Chúng tôi cũng có một loạt các [ý tưởng điên rồ](https://github.com/johnnliu/contract-register/issues) được liệt kê cho Sổ đăng ký Hợp đồng. Vì vậy, nếu bạn muốn có được bàn tay của bạn bẩn và đi, chúng tôi đang thực hiện các yêu cầu kéo!

## Tham gia ngay hôm nay

Thời gian để tham gia luôn là bây giờ (hoặc ngay khi bạn có thể). Ở đây, chúng tôi trình bày hai tháng làm việc thể hiện nỗ lực hết mình của chúng tôi nhằm thúc đẩy các công nghệ web hiện đại và SharePoint như một nền tảng. 

<!--EndFragment-->