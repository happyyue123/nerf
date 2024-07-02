本项目主要通过nerf进行3d模型渲染， 代码有LLFF数据集转换、NERF模型。效果为，通过拍摄一组图片，使用colmap提取参数，可以渲染成3d模型。
代码使用指南：
配置依赖
LLFF
'''
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple scikit-image
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple imageio
'''
nerf
'''
pip install -r requirements.txt
'''
提前准备：拍摄一组平移视角或者360度环绕视角的图片，并使用colmap转换为相机参数
1. 在LLFF文件夹下data文件夹中建立一个文件夹比如cf，cf下新建文件夹images、sprase。将图片放入images文件夹中，在sprase文件夹下新建0文件夹，将colmap相机参数放入0
文件夹中， 将colmap导出的db文件放入cf文件夹中，数据结构如图所示：
2. 运行LLFF中的imgs2pose.py,得到一个npy文件
''' 
python imgs2pose.py 'data/cy

'''
3. 将cy文件整体移动到 文件夹下，添加config运行run_nerf.py --config config COLMAP_test.txt
4. 如果像测试模型效果，则运行run_nerf.py --config config COLMAP_test.txt --render only
