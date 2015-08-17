# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Kobuki-specific ROS plugins for Gazebo."
url='http://ros.org/wiki/kobuki_gazebo_plugins'

pkgname='ros-hydro-kobuki-gazebo-plugins'
pkgver='0.3.2'
_pkgver_patch=1
arch=('any')
pkgrel=2
license=('BSD')

ros_makedepends=(ros-hydro-sensor-msgs
  ros-hydro-roscpp
  ros-hydro-geometry-msgs
  ros-hydro-catkin
  ros-hydro-nav-msgs
  ros-hydro-tf
  ros-hydro-kobuki-msgs
  ros-hydro-std-msgs
  ros-hydro-gazebo-ros)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  boost)

ros_depends=(ros-hydro-sensor-msgs
  ros-hydro-roscpp
  ros-hydro-geometry-msgs
  ros-hydro-nav-msgs
  ros-hydro-tf
  ros-hydro-kobuki-msgs
  ros-hydro-std-msgs
  ros-hydro-gazebo-ros)
depends=(${ros_depends[@]}
  boost)

_tag=release/hydro/kobuki_gazebo_plugins/${pkgver}-${_pkgver_patch}
_dir=kobuki_gazebo_plugins
source=("${_dir}"::"git+https://github.com/yujinrobot-release/kobuki_desktop-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
