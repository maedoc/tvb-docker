FROM maedoc/fs-mne-env
MAINTAINER Marmaduke Woodman <mmwoodman@gmail.com>

RUN apt-get update && apt-get install -y wget \
  && wget -O- http://neuro.debian.net/lists/xenial.de-m.full | tee /etc/apt/sources.list.d/neurodebian.sources.list \
  && apt-key adv --recv-keys --keyserver hkp://pool.sks-keyservers.net:80 0xA5D32F012649A5A9 \
  && apt-get update

RUN apt-get install -y g++ libeigen3-dev git python python-numpy zlib1g-dev \
	cmake tcsh libeigen3-dev liblapack-dev libblas-dev libssl-dev fsl-complete \
        libhdf5-dev zlib1g-dev libmatio-dev libopenblas-dev

WORKDIR /opt
RUN git clone https://github.com/mrtrix3/mrtrix3
RUN cd mrtrix3 && ./configure -nogui && ./build

RUN git clone https://github.com/openmeeg/openmeeg

RUN apt-get install -y liblapacke-dev
RUN cd openmeeg/OpenMEEG && \
    mkdir build && cd build && \
    cmake -DBUILD_TESTING=ON -DCMAKE_BUILD_TYPE=Release \
        -DENABLE_PYTHON=OFF -DCMAKE_INSTALL_PREFIX=/usr/local \
        -DBLASLAPACK_IMPLEMENTATION="OpenBLAS" \
        -DBUILD_DOCUMENTATION=OFF -DBUILD_TUTORIALS=OFF .. && \
    make -j && \
    make test && \
    make install

RUN curl -O https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
RUN bash Miniconda2-latest-Linux-x86_64.sh -b -p /opt/conda
ENV PATH /opt/conda/bin:$PATH
RUN conda install -c conda-forge jupyterlab \
 && conda install nomkl numpy numexpr numba matplotlib scipy cython scikit-learn \
 && pip install gdist psutil networkx

RUN git clone https://github.com/the-virtual-brain/tvb-library
RUN git clone https://github.com/the-virtual-brain/tvb-data

ENV PYTHONPATH /opt/tvb-library:/opt/tvb-data:$PYTHONPATH

RUN pip install nibabel nilearn mne

ENV LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH \
    PATH=/opt/mrtrix3/bin:$PATH

ENV \
 FSLDIR=/usr/share/fsl/5.0 \
 FSLBROWSER=/etc/alternatives/x-www-browser \
 FSLLOCKDIR= \
 FSLMACHINELIST= \
 FSLMULTIFILEQUIT=TRUE \
 FSLOUTPUTTYPE=NIFTI_GZ \
 FSLREMOTECALL= \
 FSLTCLSH=/usr/bin/tclsh \
 FSLWISH=/usr/bin/wish \
 LD_LIBRARY_PATH=/usr/lib/fsl/5.0:$LD_LIBRARY_PATH \
 PATH=/usr/lib/fsl/5.0:/usr/share/fsl/5.0/bin:$PATH \
 POSSUMDIR=/usr/share/fsl/5.0
