FROM maedoc/fs-mne-data
MAINTAINER Marmaduke Woodman <mmwoodman@gmail.com>

# env vars after sourcing FreeSurferEnv.sh & mne_setup_sh
ENV FIX_VERTEX_AREA= \
    FMRI_ANALYSIS_DIR=/opt/freesurfer/fsfast \
    FREESURFER_HOME=/opt/freesurfer \
    FSFAST_HOME=/opt/freesurfer/fsfast \
    FSF_OUTPUT_FORMAT=nii.gz \
    FS_OVERRIDE=0 \
    LOCAL_DIR=/opt/freesurfer/local \
    MINC_BIN_DIR=/opt/freesurfer/mni/bin \
    MINC_LIB_DIR=/opt/freesurfer/mni/lib \
    MNEROOT=/opt/MNE-2.7.0-3106-Linux-x86_64 \
    MNE_BIN_PATH=/opt/MNE-2.7.0-3106-Linux-x86_64/bin \
    MNE_LIB_PATH=/opt/MNE-2.7.0-3106-Linux-x86_64/lib \
    MNE_ROOT=/opt/MNE-2.7.0-3106-Linux-x86_64 \
    MNI_DATAPATH=/opt/freesurfer/mni/data \
    MNI_DIR=/opt/freesurfer/mni \
    MNI_PERL5LIB=/opt/freesurfer/mni/share/perl5 \
    OS=Linux \
    PERL5LIB=/opt/freesurfer/mni/share/perl5 \
    SUBJECTS_DIR=/opt/freesurfer/subjects \
    XUSERFILESEARCHPATH=/opt/MNE-2.7.0-3106-Linux-x86_64/share/app-defaults/%N \
    LD_LIBRARY_PATH=/opt/MNE-2.7.0-3106-Linux-x86_64/lib \
    PATH=/opt/MNE-2.7.0-3106-Linux-x86_64/bin:/opt/freesurfer/bin:/opt/freesurfer/fsfast/bin:/opt/freesurfer/tktools:/opt/freesurfer/mni/bin:$PATH
