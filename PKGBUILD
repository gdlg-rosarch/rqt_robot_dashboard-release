# Script generated with Bloom
pkgdesc="ROS - rqt_robot_dashboard provides an infrastructure for building robot dashboard plugins in rqt."
url='http://wiki.ros.org/rqt_robot_dashboard'

pkgname='ros-lunar-rqt-robot-dashboard'
pkgver='0.5.7_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-lunar-catkin'
)

depends=('ros-lunar-diagnostic-msgs'
'ros-lunar-python-qt-binding>=0.2.19'
'ros-lunar-qt-gui'
'ros-lunar-rospy'
'ros-lunar-rqt-console>=0.3.1'
'ros-lunar-rqt-gui'
'ros-lunar-rqt-gui-py'
'ros-lunar-rqt-nav-view'
'ros-lunar-rqt-robot-monitor'
)

conflicts=()
replaces=()

_dir=rqt_robot_dashboard
source=()
md5sums=()

prepare() {
    cp -R $startdir/rqt_robot_dashboard $srcdir/rqt_robot_dashboard
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

